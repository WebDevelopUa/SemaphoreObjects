# SemaphoreObjects


*semaphore.cpp*: ���������� ����� ����� ��� ����������� ����������.

https://msdn.microsoft.com/en-us/library/windows/desktop/ms686946(v=vs.85).aspx


� ��������� ������� ������ �������� ������������ ��� ����������� ���������� �������, ������� ����� ��������� ������������ ������.

��-������, �� ���������� ������� **CreateSemaphore** ��� �������� �������� � �������� ���������� � ������������� ���������, ����� �� ���������� ������� **CreateThread** ��� �������� �������.

������ ��� ����� ���������� ��������� ������, �� ���������� ������� **WaitForSingleObject**, ����� ����������, ��������� �� ��� ����� �������� ��� ������.

�������� ����-���� ������� �������� ���������� �� ����, ������� ������� ���������� ������������, ���� ������� ��������� � ��������� ��������������.

**WaitForSingleObject** ��������� ���������� �������� �� �������.

����� ����� ��������� ������, �� ���������� ������� **ReleaseSemaphore**, ����� ��������� ���� ��������, ��� ����� �������� ������� ���������� ������ ��������� ������.


***


The following example uses a semaphore object to limit the number of threads that can perform a particular task. 

First, it uses the **CreateSemaphore** function to create the semaphore and to specify initial and maximum counts, then it uses the **CreateThread** function to create the threads.

Before a thread attempts to perform the task, it uses the **WaitForSingleObject** function to determine whether the semaphore's current count permits it to do so. 

The wait function's time-out parameter is set to zero, so the function returns immediately if the semaphore is in the nonsignaled state. 

**WaitForSingleObject** decrements the semaphore's count by one.

When a thread completes the task, it uses the **ReleaseSemaphore** function to increment the semaphore's count, thus enabling another waiting thread to perform the task.