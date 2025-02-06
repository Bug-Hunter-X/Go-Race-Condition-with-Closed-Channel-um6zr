# Go Race Condition with Closed Channel

This repository demonstrates a common race condition in Go programs involving channels.  The program uses multiple goroutines to receive from a channel that is closed before all goroutines can consume from it. This results in undefined behavior.

## Bug Description

The `bug.go` file contains a program that launches multiple goroutines. Each goroutine attempts to receive a value from a shared channel.  The channel is closed before all goroutines have had a chance to receive a value. This race condition leads to unpredictable behavior: some goroutines might receive a default value (0 for int), while others might block indefinitely.

## Solution

The `bugSolution.go` demonstrates a solution to address this race condition.  This solution ensures that all goroutines have a chance to receive from the channel before it's closed.