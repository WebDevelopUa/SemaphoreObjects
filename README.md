# SemaphoreObjects



*semaphore.cpp*: определяет точку входа для консольного приложения.

https://msdn.microsoft.com/en-us/library/windows/desktop/ms686946(v=vs.85).aspx


В следующем примере объект семафора используется для ограничения количества потоков, которые могут выполнять определенную задачу.

Во-первых, он использует функцию **CreateSemaphore** для создания семафора и указания начального и максимального счетчиков, затем он использует функцию **CreateThread** для создания потоков.

Прежде чем поток попытается выполнить задачу, он использует функцию **WaitForSingleObject**, чтобы определить, позволяет ли это счету семафора это делать.

Параметр тайм-аута функции ожидания установлен на ноль, поэтому функция немедленно возвращается, если семафор находится в состоянии несоответствия.

**WaitForSingleObject** уменьшает количество семафора на единицу.

Когда поток завершает задачу, он использует функцию **ReleaseSemaphore**, чтобы увеличить счет семафора, тем самым позволяя другому ожидающему потоку выполнять задачу.




***


The following example uses a semaphore object to limit the number of threads that can perform a particular task. 

First, it uses the **CreateSemaphore** function to create the semaphore and to specify initial and maximum counts, then it uses the **CreateThread** function to create the threads.

Before a thread attempts to perform the task, it uses the **WaitForSingleObject** function to determine whether the semaphore's current count permits it to do so. 

The wait function's time-out parameter is set to zero, so the function returns immediately if the semaphore is in the nonsignaled state. 

**WaitForSingleObject** decrements the semaphore's count by one.

When a thread completes the task, it uses the **ReleaseSemaphore** function to increment the semaphore's count, thus enabling another waiting thread to perform the task.
