# Meta
[meta]: #meta
- Name: Add Status to RFC Metadata
- Start Date: 2021-07-14
- Author(s): @aemengo, @ekcasey
- Status: Approved | On Hold
- RFC Pull Request: (leave blank)
- CNB Pull Request: (leave blank)
- CNB Issue: (leave blank)
- Supersedes: (put "N/A" unless this replaces an existing RFC, then link to that RFC)

# Summary
[summary]: #summary

This is a proposal to add a `Status:` field to the `Meta` section of the RFC template.

# Definitions
[definitions]: #definitions

**Core team:** The party that votes on the approval of RFCs.

# Motivation
[motivation]: #motivation

This RFC formally introduces the **"On Hold"** status for an RFC, in a way that's clear to the community.

# What it is
[what-it-is]: #what-it-is

A new `Status:` field in the `Meta` section of the RFC template. See [#meta](#meta) for example.

The acceptable values are distinguished in the following ways:
- **Approved**: The Core team has approved the RFC and is accepting PRs for its implementation.
- **On Hold**: The Core team has approved the RFC, but PRs are currently not being accepted for its implementation. A reason must be provided in the RFC.

The `Status:` field does not intend to reflect states that are already implied by the RFC process. Examples including: *Draft*, *In Review*, *Closed*, etc.

# How it Works
[how-it-works]: #how-it-works

We will add the following to the RFC `Meta` section template:

```
- Status: Approved | On Hold
```

When an RFC is approved, the [../merge-rfc.sh](../merge-rfc.sh) script reflects the change like so:

```
- Status: **Approved** | On Hold
```

When an RFC is put on hold (_via Pull Request_) then change is reflected like so:

```
- Status: Approved | **On Hold**
```

# Drawbacks
[drawbacks]: #drawbacks

* This field might get out of sync if not properly maintained.

# Alternatives
[alternatives]: #alternatives

- Communicate "On Hold" status through word of mouth
- Reject the "On Hold" status altogether

# Prior Art
[prior-art]: #prior-art

- TensorFlow has an ["Status" field](https://github.com/tensorflow/community/blob/master/rfcs/yyyymmdd-rfc-template.md)

# Unresolved Questions
[unresolved-questions]: #unresolved-questions

- Should **"Implemented"** be one of the accepted values?
    - Perhaps, but then what's the process of keeping the _Implemented_ status in sync?

- How do we retroactively add a **Status:** field to prior RFCs?
    - Manually?

- How do we validate the [#meta](#meta) section of prior RFCs?
    - Perhaps we make a [../validate-rfcs.sh](../validate-rfcs.sh) script that lints the **#meta** section of all rfcs?