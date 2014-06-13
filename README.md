# mod_s2soutinjection

## Introduction

This Prosody plugin lets you manually override dns records used for a remote host.

## Usage

Simply add `s2soutinjection` to your `modules_enabled` list to enable. Then add the `s2s_connect_overrides` option to the global section.

## Configuration

The `s2s_connect_overrides` option can be used as follows:

```lua
s2s_connect_overrides = {
  ["example.com"] = {"localhost", 5000};
  ["jabber.org"] = {"1.2.3.4", 5001};
  ["gmail.com"] = {"xmpp-server.l.google.com"};
};
```
The format for individual items is
```lua
["remote-hostname"] = {IP or HostName, Port-optionnal};
```

## Compatibility

| Version | test |
|---------|------|
| 0.9 | Works |
| <=0.8 | NO |

## How it works

The module replaces the lookup function of the net.adns module with its own. The original is set back when the module is unloaded.
