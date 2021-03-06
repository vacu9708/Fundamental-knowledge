**A garbage collector** constantly monitors all allocated memory and reclaims memory which was allocated, but is no longer referenced.<br>
In traditional languages, memory has to be managed manually by the programmer, but it turned out that is too difficult. That is why the garbage collector appeared.<br>

Automatic memory management is performed through the concept **"reachability"**. The reachability means that a piece of allocated memory can be reached and used.<br>
If an object no longer has any reference to it, it means the object is a waste of memory and should be deleted.

### Reachable object
![image](https://user-images.githubusercontent.com/67142421/177013694-8add3600-ae4d-47ad-899f-2611edaf7317.png)

### Unreachable object
![image](https://user-images.githubusercontent.com/67142421/178157740-cd8b3828-ca89-4a37-a89c-20a26c80d12b.png)

## Optimization of garbage collection
>A garbage collection operation is a CPU-demanding task. There is a need for optimization.
**Generational collection** : Objects are divided into "young objects" and "old objects(or permanent objects)".<br>
Garbage collection can be optimized based on the fact that the majority of objects created newly become unreachable.<br>

* The garbage collection monitors and deletes young objects actively. This is called Minor Gabarge Collection.
* Objects created early that survive minor collection are moved to "old objects", Old objects are monitored less frequently than young objects, which is called
 Major Garbage Collection.

**Idle-time collection** : Garbage collection is performed only when the CPU is idle to minimize the latency and exploit CPU idle times.
