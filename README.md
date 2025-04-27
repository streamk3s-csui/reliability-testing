# Reliability Testing

This repository contains the source code for the injected chaos tests used to test StreamK3s' reliability as a data processing platform. An assessment of performance, data integrity, and data availability will be conducted using the tests contained in this repository.

As the platform uses companion containers as sidecars to the generator (producer) and grouper (consumer), point of failures are introduced as the data must pass through these companion containers. These containers are at risk of pod failures, network latency, and HTTP request failures among others. We will focus on the first two failure scenarios, as they are more common than the last scenario, and are more determinant on how the platform is designed instead of other external factors. 

In this repository, we present how we simulated these failures on the platform. We utilized [Chaos Mesh](https://chaos-mesh.org/) to inject failure scenarios that might happen on production environments. Specifically, we used the  `PodChaos` and `NetworkChaos` fault types, which you can read about more [here](https://chaos-mesh.org/docs/simulate-pod-chaos-on-kubernetes/) and [here](https://chaos-mesh.org/docs/simulate-network-chaos-on-kubernetes/).

## Quickstart

1. Clone this repository.
2. `cd` into repository and run `kubectl apply -f` on the failure you want to inject.