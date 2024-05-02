# Simple BGP Router Project

## Overview

This project involves building a simple BGP (Border Gateway Protocol) router in Python. The router is capable of managing multiple sockets in a simulated network, handling route announcements and withdrawals, forwarding data packets, and ensuring correctness and performance.

## High-Level Approach

The router is implemented in Python and uses standard libraries for network communication and data handling. The main components of the router include:

### Core Functionalities

- **Update Message Handling (`handle_update`)**: Processes 'update' messages to update the forwarding table with new routes.
- **Data Message Handling (`handle_data`)**: Forwards data packets based on the best route determined by BGP route selection rules.
- **Withdraw Message Handling (`handle_withdraw`)**: Processes 'withdraw' messages to remove routes from the forwarding table.
- **Route Aggregation (`aggregate_forwarding_table`)**: Optimizes routing by aggregating routes in the forwarding table.

## Challenges Faced

### ASN in Milestone

Initially, we did not realize that we had to add the ASN in the milestone, which caused difficulties in diagnosing errors.

- **Solution**: We added the ASN to the milestone, which resolved the issues we were facing with tests 1-1-simple-send.conf and 1-2-simple-send.conf.

### Withdraw Message Confusion

We faced confusion with the withdraw message, particularly when routes advertised by different neighbors needed to be handled correctly.

- **Solution**: We ensured that the router only withdraws the route received from the neighbor that sent the withdraw message while keeping other routes intact.

### Dropping Messages

Implementing the logic for dropping messages based on the legal forwarding check was challenging.

- **Solution**: We implemented checks to ensure that data messages are only forwarded if the source router is a customer or the destination is a customer.

## Testing

We ran our code against the tests which are under the `configs` folder and placed debug statements throughout to edit/fix the code in order to pass the tests. This involved:

- **Test Execution**: Running the router against various test configurations to simulate different network scenarios.
- **Debugging**: Adding debug statements to identify and fix issues in the code, ensuring that the router behaves as expected.
- **Validation**: Verifying that the router correctly handles 'update', 'data', and 'withdraw' messages, and that it makes correct forwarding decisions.