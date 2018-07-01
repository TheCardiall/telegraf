
- ts: 
- measurement & fields:
  - 
- tags:
  - 

#### kube_configmap
- ts: configmap created
- measurement & fields:
  - gauge (always 1)
- tags:
  - namespace
  - configmap
  - resource_version

#### kube_cronjob
- ts: now
- measurement & fields:
  - status_active ( # of active jobs)
  - spec_starting_deadline_seconds
  - next_schedule_time
  - created
  - status_last_schedule_time
- tags:
  - namespace
  - cronjob
  - schedule
  - concurrency_policy
  - label_* 

#### kube_daemonset
- ts: daemonset created
- measurement & fields:
  - metadata_generation
- tags:
  - namespace
  - daemonset
  - label_*

#### kube_daemonset_status
- ts: now
- measurement & fields:
  - current_number_scheduled
  - desired_number_scheduled
  - number_available
  - number_misscheduled
  - number_ready
  - number_unavailable
  - updated_number_scheduled
- tags:
  - namespace
  - daemonset
  - label_*

#### kube_deployment
- ts: deployment created
- measurement & fields:
  - spec_replicas
  - metadata_generation
  - spec_strategy_rollingupdate_max_unavailable
  - spec_strategy_rollingupdate_max_surge
- tags:
  - namespace
  - deployment
  - spec_paused ("true", "false")

#### kube_deployment_status
- ts: now
- measurement & fields:
  - replicas
  - replicas_available
  - replicas_unavailable
  - replicas_updated
  - observed_generation
- tags:
  - namespace
  - deployment

#### kube_endpoint
- ts: endpoint created
- measurement & fields:
  - address_available
  - address_not_ready
- tags:
  - namespace
  - endpoint

#### kube_hpa
- ts: hpa created
- measurement & fields:
  - metadata_generation
  - spec_max_replicas
  - spec_min_replicas
- tags:
  - namespace
  - hpa
  - label_*

#### kube_hpa_status
- ts: now
- measurement & fields:
  - current_replicas
  - desired_replicas
  - condition_true (1 = "true", 0 = "false")
  - condition_false (1 = "true", 0 = "false")
  - condition_unkown
- tags:
  - namespace
  - hpa
  - condition ("true", "false", "unkown")
  


#### kube_pod

- ts: pod created
- measurement & fields:
  - gauge (always 1)
- tags:
  - namesapce
  - pod
  - node
  - created_by_kind
  - created_by_name
  - owner_kind
  - owner_name
  - owner_is_controller ("true", "false")
  - label_*

#### kube_pod_status

- ts: now
- measurement & fields:
  - status_phase_pending (1 = "true", 0 = "false")
  - status_phase_succeeded (1 = "true", 0 = "false")
  - status_phase_failed (1 = "true", 0 = "false")
  - status_phase_running (1 = "true", 0 = "false")
  - status_phase_unknown (1 = "true", 0 = "false")
  - completion_time
  - scheduled_time
- tags:
  - namesapce
  - pod
  - node
  - host_ip
  - pod_ip
  - status_phase ("pending", "succeeded", "failed", "running", "unknown")
  - ready ("true", "false")
  - scheduled ("true", "false")

#### kube_pod_container

- ts: now
- measurement & fields:
  - status_restarts_total
  - status_waiting (1 = "true", 0 = "false")
  - status_running (1 = "true", 0 = "false")
  - status_terminated (1 = "true", 0 = "false")
  - status_ready (1 = "true", 0 = "false")
  - resource_requests_cpu_cores
  - resource_requests_memory_bytes
  - resource_requests_storage_bytes
  - resource_requests_ephemeral_storage_bytes
  - resource_limits_cpu_cores
  - resource_limits_memory_bytes
  - resource_limits_storage_bytes
  - resource_limits_ephemeral_storage_bytes
- tags:
  - namespace
  - pod_name
  - node_name
  - container
  - image
  - image_id
  - container_id
  - status_waiting_reason
  - status_terminated_reason


#### kube_pod_volume
- ts: now
- measurement & fields:
  - read_only (1 = "true", 0 = "false")
- tags:
  - namespace
  - pod
  - volume
  - persistentvolumeclaim
