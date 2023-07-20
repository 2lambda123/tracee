
# waitpid

## Intro
waitpid - wait for a process to change its state

## Description
The waitpid() system call suspends execution of the calling process until a
child process specified by pid argument has changed state. By giving the
WNOHANG or WUNTRACED options to waitpid() call, the calling process can
specify that it should return immediately if there is no process state
change. The status pointer argument may be specified as NULL.

## Arguments
* `pid`:`pid_t` - Specifies a set of child processes for which to wait.
* `status`:`int*`[U] - A pointer to an integer into which status information
about the child process will be stored. This can be NULL if the calling process
is not interested in this information.
* `options`:`int` - May be specified to include WNOHANG or WUNTRACED, which
modify the behavior of the waitpid() system call.

### Available Tags
* U - Originated from user space (for example, pointer to user space memory used to get it)

## Hooks
### do_wait()
#### Type
KProbes
#### Purpose
Used to monitor usage of waitpid in the system.

## Example Use Case
This event can be used to monitor and detect when a process with a specified
pid has changed state. 

## Issues
None.

## Related Events
- fork()
- execve()
- signal()

> This document was automatically generated by OpenAI and needs review. It might
> not be accurate and might contain errors. The authors of Tracee recommend that
> the user reads the "events.go" source file to understand the events and their
> arguments better.