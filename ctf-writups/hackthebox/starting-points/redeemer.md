# Redeemer

start with Full Nmap scan then check Use -A  <mark style="color:red;">`enable OS detection and version scanning`</mark>

```bash
#Nmap 
sudo nmap -p-  --open -T4 -vv  -Pn 10.129.64.145   
PORT     STATE SERVICE REASON                                                                                                                                            
6379/tcp open  redis   syn-ack ttl 63     
-------------------------------------------

sudo nmap -p6379 -sCV   -Pn 10.129.64.145 
PORT     STATE SERVICE VERSION
6379/tcp open  redis   Redis key-value store 5.0.7

```

As we can see the service running is Redis so the Question now what is Redis?&#x20;

**Redis is an open-source, in-memory data store used by millions of developers as a database, cache, streaming engine, and message broker.**

## Redis Exploitation

we can use <mark style="color:purple;">**Netcat**</mark>** ** or ** **<mark style="color:purple;">**redis-tools '**</mark>

{% code lineNumbers="true" %}
```bash
// we will use redis-cli 
redli -h 10.129.64.145 -p 6379
Connected to 5.0.7                                                                                                                  
> info   # Gather info 
redis_version:5.0.7                                                                                                                 
redis_git_sha1:00000000                                                                                                             
redis_git_dirty:0                                                                                                                   
redis_build_id:66bd629f924ac924                                                                                                     
redis_mode:standalone                                                                                                               
os:Linux 5.4.0-77-generic x86_64                                                                                                    
arch_bits:64                                                                                                                        
multiplexing_api:epoll                                                                                                              
atomicvar_api:atomic-builtin                                                                                                        
gcc_version:9.3.0                                                                                                                   
process_id:747                                                                                                                      
run_id:4c9a6bf177f0197c135185eadc375ab4cecc2d7a                                                                                     
tcp_port:6379                                                                                                                       
uptime_in_seconds:2465                                                                                                              
uptime_in_days:0                                                                                                                    
hz:10                                                                                                                               
configured_hz:10                                                                                                                    
lru_clock:4889569                                                                                                                   
executable:/usr/bin/redis-server                                                                                                    
config_file:/etc/redis/redis.conf                                                                                                   
                                                                                                                                    
# Clients                  
connected_clients:1         
client_recent_max_input_buffer:2
client_recent_max_output_buffer:0                                                                                                                          
blocked_clients:0               
                                                                  
# Memory                           
used_memory:859624         
used_memory_human:839.48K          
used_memory_rss:5353472            
used_memory_rss_human:5.11M        
used_memory_peak:859624                   
used_memory_peak_human:839.48K            
used_memory_peak_perc:100.00%             
used_memory_overhead:846142               
used_memory_startup:796224                
used_memory_dataset:13482                     
used_memory_dataset_perc:21.26%               
allocator_allocated:1171320                   
allocator_active:1445888                      
allocator_resident:4218880                    
total_system_memory:2084024320                
total_system_memory_human:1.94G                                                                                     
used_memory_lua:41984                                     
used_memory_lua_human:41.00K                              
used_memory_scripts:0                                     
used_memory_scripts_human:0B                              
number_of_cached_scripts:0                                
maxmemory:0                                               
maxmemory_human:0B                                        
maxmemory_policy:noeviction                               
allocator_frag_ratio:1.23                                 
allocator_frag_bytes:274568                               
allocator_rss_ratio:2.92                                  
allocator_rss_bytes:2772992                                       
rss_overhead_ratio:1.27                                           
rss_overhead_bytes:1134592                                        
mem_fragmentation_ratio:6.55                                      
mem_fragmentation_bytes:4535856                                   
mem_not_counted_for_evict:0                                       
mem_replication_backlog:0                                                                                           
mem_clients_slaves:0                                              
mem_clients_normal:49694                                          
mem_aof_buffer:0                                                  
mem_allocator:jemalloc-5.2.1                                      
active_defrag_running:0                                           
lazyfree_pending_objects:0                                                                   
                                                                                             
# Persistence                                                                                
loading:0                                                                                    
rdb_changes_since_last_save:0                                                                
rdb_bgsave_in_progress:0                                                                     
rdb_last_save_time:1665832389                                                                
rdb_last_bgsave_status:ok                                                                    
rdb_last_bgsave_time_sec:0                                                                   
rdb_current_bgsave_time_sec:-1                                                               
rdb_last_cow_size:405504                                                                     
aof_enabled:0                                                                                
aof_rewrite_in_progress:0                                                                    
aof_rewrite_scheduled:0                                                                      
aof_last_rewrite_time_sec:-1                                                                 
aof_current_rewrite_time_sec:-1                                                              
aof_last_bgrewrite_status:ok                                                                 
aof_last_write_status:ok                                                                     
aof_last_cow_size:0                                                                          
                                                                                             
# Stats                                                                                                             
total_connections_received:8                                                                                        
total_commands_processed:8                                                                                          
instantaneous_ops_per_sec:0                                                                                         
total_net_input_bytes:480                                                                                           
total_net_output_bytes:13468                                                                                        
instantaneous_input_kbps:0.00                                                                                       
instantaneous_output_kbps:0.00                                                                                      
rejected_connections:0                                                                                              
sync_full:0                                                                                                                                                
sync_partial_ok:0                                                                                                   
sync_partial_err:0                                                                                                  
expired_keys:0                                                                                                      
expired_stale_perc:0.00                                                                                             
expired_time_cap_reached_count:0                                                                                    
evicted_keys:0                                                                                                      
keyspace_hits:0                                                                                                     
keyspace_misses:0                                                                                                   
pubsub_channels:0                                                                                                   
pubsub_patterns:0                                                                                                   
latest_fork_usec:661                                                                                                
migrate_cached_sockets:0                                                                                                                                   
slave_expires_tracked_keys:0                                                                                        
active_defrag_hits:0                                                                                                
active_defrag_misses:0                                                                                              
active_defrag_key_hits:0                                                                                            
active_defrag_key_misses:0                                                                                          

# Replication                                                                                                       
role:master                                                                                                         
connected_slaves:0                                                                                                                                         
master_replid:e06ffb83fffaab8b13a62f173bec8474636c4154                                                              
master_replid2:0000000000000000000000000000000000000000                                                             
master_repl_offset:0                                                                                                                                       
second_repl_offset:-1                                                                                               
repl_backlog_active:0                                                                                                                                      
repl_backlog_size:1048576                                                                                                                                  
repl_backlog_first_byte_offset:0                                                                                                                           
repl_backlog_histlen:0                                                                                                                                     

# CPU                                                                                                                                                      
used_cpu_sys:2.502319                                                                                                                                      
used_cpu_user:2.698087                                                                                                                                     
used_cpu_sys_children:0.003921                                                                                                                             
used_cpu_user_children:0.000000                                                                                                                            

# Cluster                                                                                                                                                  
cluster_enabled:0                                                                                                                                          

# Keyspace                                                      
```
{% endcode %}

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
