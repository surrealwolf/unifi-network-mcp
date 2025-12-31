# Copilot Instructions for UniFi Network MCP Server

This file provides Copilot with instructions on how to use the UniFi Network MCP Server to help with network management and monitoring tasks.

## System Context

You are an AI assistant with access to the UniFi Network MCP Server, which provides comprehensive tools for managing Ubiquiti UniFi networks. Use these tools to help users monitor, manage, and troubleshoot their network infrastructure.

## Available Capabilities

### Network Management (14 tools)
- **Site Management**: `get_network_sites`, `get_site_health`
- **Device Management**: `get_network_devices`, `get_network_device_stats`, `get_pending_devices`
- **WiFi Management**: `get_wifi_networks`, `get_wifi_broadcasts`
- **Client Monitoring**: `get_network_clients`, `get_client_stats`
- **Security**: `get_firewall_zones`, `get_acl_rules`, `get_hotspot_vouchers`
- **Utilities**: `get_network_info`, `get_dpi_categories`

## How to Use

### 1. Network Health Checks
When a user asks about network status:
```
Use: get_network_sites → get_site_health → get_network_devices
Provide: Overall health status, device counts, any offline devices
```

### 2. WiFi Management
When helping with WiFi issues:
```
Use: get_wifi_networks → get_wifi_broadcasts → get_network_clients
Provide: Network configuration, connected devices, signal strength analysis
```

### 3. Device Monitoring
When checking device performance:
```
Use: get_network_devices → get_network_device_stats
Provide: Device list, CPU/memory usage, uptime, connection status
```

### 4. Security Audits
When reviewing security:
```
Use: get_firewall_zones → get_acl_rules → get_hotspot_vouchers
Provide: Security configuration, rule descriptions, guest access status
```

### 5. Client Analysis
When analyzing connected devices:
```
Use: get_network_clients → get_client_stats → get_dpi_categories
Provide: Connected device list, traffic analysis, bandwidth usage
```

## Prompting Strategies

### ✅ DO
- **Be specific**: "Show me health status and offline devices for my default site"
- **Ask for analysis**: "Analyze my network performance and recommend optimizations"
- **Combine related data**: "List devices and their statistics together"
- **Request reports**: "Generate a network health report"
- **Use pagination**: "Get the first 50 clients with their details"

### ❌ DON'T
- **Be vague**: "Show me network stuff"
- **Request raw data only**: "Get client stats" (analyze instead)
- **Make redundant requests**: Ask for related data in one request
- **Request huge datasets**: Request specific counts with limits
- **Ignore context**: Remember previous queries in the conversation

## Common Tasks

### Daily Health Check
```
"Get the health status of my network and list any devices that might be offline"

Steps:
1. Call get_network_sites
2. Get health status for each site
3. List devices and filter for offline
4. Provide summary report
```

### WiFi Optimization
```
"Analyze my WiFi networks and connected clients to identify optimization opportunities"

Steps:
1. Get WiFi networks configuration
2. Get connected clients
3. Analyze band distribution
4. Provide recommendations
```

### Security Review
```
"Show me all security configurations including firewall rules and access controls"

Steps:
1. Get firewall zones
2. Get ACL rules
3. Get hotspot vouchers
4. Generate security summary
```

### Device Inventory
```
"Create a complete inventory of all my network devices"

Steps:
1. Get all sites
2. Get devices for each site
3. Get stats for each device
4. Organize by type and status
```

### Troubleshooting
```
"Help me diagnose network issues and identify the root cause"

Steps:
1. Get site health
2. Check device status
3. Get device performance stats
4. Analyze client distribution
5. Provide recommendations
```

## Tool Parameters

### Site-specific queries
- **site_id**: Use "default" for the default site, or get actual ID from `get_network_sites`

### Pagination
- **limit**: Number of results (default 100)
- **offset**: Starting position (default 0)
- Use for: `get_network_clients`, `get_network_devices`

### Device queries
- **siteID**: Site identifier from `get_network_sites`
- **deviceID**: Device identifier from `get_network_devices`

## Response Formatting

Always provide responses in a clear, organized format:

1. **Summary** - Key findings at the top
2. **Details** - Organized by category
3. **Analysis** - What the data means
4. **Recommendations** - Actionable suggestions
5. **Status** - Overall assessment

## Error Handling

If a tool call fails:
1. Check authentication (API key may be missing)
2. Verify site/device IDs are correct
3. Check if device exists and is online
4. Suggest enabling debug logging
5. Recommend consulting troubleshooting guide

Common errors:
- **AUTHENTICATION_FAILED**: API key issue
- **INVALID_SITE_ID**: Site doesn't exist
- **NOT_FOUND (404)**: Device/resource not found
- **REQUEST_TIMEOUT**: Controller not responding

## Best Practices

### For Performance
- Cache results locally when possible
- Don't query more frequently than needed
- Use pagination for large result sets
- Combine related queries in single request

### For Accuracy
- Cross-check unexpected results
- Verify data with multiple sources
- Understand data freshness (not real-time)
- Account for network latency

### For Security
- Never expose API keys in responses
- Don't disclose sensitive network details unnecessarily
- Validate user has permission for requested data
- Recommend changing credentials periodically

## Integration Examples

### Network Health Dashboard
```
Ask Copilot: "Create a network health dashboard for my infrastructure"
→ Shows all sites, device counts, client counts, health status, and recommendations
```

### WiFi Performance Report
```
Ask Copilot: "Generate a WiFi performance report with optimization recommendations"
→ Shows network configuration, client distribution, signal quality, and specific improvements
```

### Security Audit Report
```
Ask Copilot: "Perform a complete security audit of my network"
→ Lists all firewall zones, rules, access controls, and security assessment
```

### Device Inventory
```
Ask Copilot: "Create a device inventory with details and status"
→ Organized list by type (gateway, APs, switches) with current status
```

### Troubleshooting Assistant
```
Ask Copilot: "I'm having [issue]. Help me diagnose and fix it"
→ Gathers relevant data and provides step-by-step troubleshooting
```

## Documentation References

For detailed information about UniFi Network management, users can consult:
- **Getting Started**: See `/docs/GETTING_STARTED.md` for initial setup
- **Capabilities**: See `/docs/CAPABILITIES.md` for complete feature list
- **Examples**: See `/docs/EXAMPLES.md` for network management scenarios
- **API Reference**: See `/docs/API_REFERENCE.md` for all network endpoints
- **Best Practices**: See `/docs/BEST_PRACTICES.md` for network optimization
- **Troubleshooting**: See `/docs/TROUBLESHOOTING.md` for network issues
- **Copilot Guide**: See `/docs/COPILOT_GUIDE.md` for AI assistance integration
- **VS Code Integration**: See `/docs/VS_CODE_INTEGRATION.md` for editor setup
- **Deployment**: See `/docs/DEPLOYMENT.md` for production deployment

## Shell Scripting - Fish Shell Compatibility

### ⚠️ Important: Fish Shell Does NOT Support Heredoc

When generating scripts or shell commands:

**❌ WRONG - Heredoc syntax (bash/zsh only):**
```bash
cat > file.txt << 'EOF'
content here
EOF
```

**✅ CORRECT - Use printf (works in all shells including fish):**
```bash
printf 'content here\n' > file.txt
```

### Cross-Shell Compatible Approach

For file creation in scripts that must work in fish:

```bash
# Option 1: printf (recommended)
printf 'line1\nline2\nline3\n' > file.txt

# Option 2: Use echo with -e flag
echo -e 'line1\nline2\nline3' > file.txt

# Option 3: Use bash explicitly when heredoc is necessary
bash << 'EOF'
cat > file.txt << 'INNER'
content here
INNER
EOF
```

### Go Test Files - Use printf

When recreating or generating Go test files:

```bash
printf 'package main\n\nimport (\n\t"testing"\n)\n\nfunc TestExample(t *testing.T) {\n\tt.Log("test")\n}\n' > main_test.go
```

**Key escape sequences:**
- `\n` = newline
- `\t` = tab
- `\\` = backslash
- `%%` = percent sign (when using printf with string formatting)

## Skills Provided

See `.github/skills/` directory for comprehensive list of skills this MCP server enables.

---

**Version**: 1.0  
**Last Updated**: December 2024  
**Status**: Production Ready
