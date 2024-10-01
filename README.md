<!DOCTYPE html>
<html lang="en">
<head>
    <h1>RTOS README</h1>
</head>
<body>
    <h1>RTOS</h1>
    <p><strong>RTOS</strong> is a project implementing a Real-Time Operating System (RTOS) on embedded hardware using a mix of C and Assembly. This system manages tasks, memory, and communication between processes in a resource-constrained environment, specifically targeting ARM Cortex-A9 processors and the DE1-SoC board.</p>
    <h2>Features</h2>
    <ul>
        <li><strong>Memory Management</strong>: Implements first-fit memory allocation, deallocation, and external fragmentation counting.</li>
        <li><strong>Task Management</strong>: Supports dynamic task creation, priority-based scheduling, and preemption.</li>
        <li><strong>Inter-Task Communication</strong>: Provides mailbox-based messaging for inter-task communication.</li>
        <li><strong>Interrupt Handling</strong>: UART-based interrupt handling for serial communication.</li>
    </ul>
    <h2>Directory Structure</h2>
    <ul>
        <li><strong>DE1-SoC/</strong>: Contains code for the DE1-SoC development board setup and configuration.</li>
        <li><strong>RTX/</strong>: Implements the core RTOS functionality, including task management, memory management, and inter-task messaging.</li>
        <li><strong>app/</strong>: Includes application-level test cases for memory and task management.</li>
        <li><strong>kernel/</strong>: Core kernel components, handling scheduling, memory, and system calls.</li>
    </ul>
    <h2>Getting Started</h2>
    <ol>
        <li>Clone the repository:
            <pre><code>git clone https://github.com/aeimaan/RTOS.git</code></pre>
        </li>
        <li>Set up your development environment for the DE1-SoC or the ARM Cortex-A9 processor using <strong>ARM DS</strong> and <strong>Quartus</strong>.</li>
        <li>Compile the kernel and application code using the provided makefiles or ARM DS IDE.</li>
        <li>Deploy the compiled binaries to the DE1-SoC board or ARM Cortex-A9 processor.</li>
    </ol>
    <h2>Core Components</h2>
    <h3>Memory Management</h3>
    <p>Implements dynamic memory allocation using a first-fit strategy and supports coalescence of freed memory. Key functions include:</p>
    <ul>
        <li><code>k_mem_init()</code>: Initializes memory.</li>
        <li><code>k_mem_alloc()</code>: Allocates memory.</li>
        <li><code>k_mem_dealloc()</code>: Deallocates memory.</li>
        <li><code>k_mem_count_extfrag()</code>: Counts external memory fragmentation.</li>
    </ul>
    <h3>Task Management</h3>
    <p>The RTOS supports preemptive multitasking with dynamic task creation. Key features include:</p>
    <ul>
        <li><strong>Task Scheduling</strong>: Tasks are scheduled using a strict-priority algorithm with support for task preemption.</li>
        <li><strong>Task Functions</strong>:
            <ul>
                <li><code>k_tsk_create()</code>: Creates new tasks.</li>
                <li><code>k_tsk_set_prio()</code>: Changes task priority.</li>
                <li><code>k_tsk_exit()</code>: Terminates tasks.</li>
                <li><code>scheduler()</code>: Determines the next task to run based on priority.</li>
            </ul>
        </li>
    </ul>

   <h3>Inter-Task Communication</h3>
    <p>Tasks communicate through mailboxes. Each task can send and receive messages asynchronously using:</p>
    <ul>
        <li><code>k_mbx_create()</code>: Creates a mailbox for the task.</li>
        <li><code>k_send_msg()</code>: Sends a message to another task's mailbox.</li>
        <li><code>k_recv_msg()</code>: Receives a message from the mailbox.</li>
    </ul>

  <h3>UART Interrupt Handling</h3>
    <p>The RTOS includes interrupt handling for the UART interface, allowing real-time interaction with external devices like keyboards through message passing.</p>

  <h2>Prerequisites</h2>
    <ul>
        <li><strong>Quartus</strong> and <strong>ARM DS IDE</strong> for compiling and deploying to the DE1-SoC board.</li>
        <li><strong>libc</strong> and <strong>libm</strong> for running tasks and performing system calls on the ARM Cortex-A9.</li>
    </ul>

  <h2>How to Run</h2>
    <ol>
        <li>Set up the hardware environment by connecting the DE1-SoC board or the ARM Cortex-A9 to your development machine.</li>
        <li>Compile the project with the necessary tools.</li>
        <li>Deploy the compiled files to the development board or simulator.</li>
        <li>Execute the project and observe the RTOS managing tasks and handling communication.</li>
    </ol>
</body>
</html>
