
---
title: "DnsRecordSet"
title_tag: "yandex.DnsRecordSet"
meta_desc: "Documentation for the yandex.DnsRecordSet resource with examples, input properties, output properties, lookup functions, and supporting types."
---



<!-- WARNING: this file was generated by Pulumi Docs Generator. -->
<!-- Do not edit by hand unless you're certain you know what you are doing! -->

Manages a DNS Recordset.

{{% examples %}}

## Example Usage

{{< chooser language "typescript,python,go,csharp" / >}}





{{< example csharp >}}

```csharp
using Pulumi;
using Yandex = Pulumi.Yandex;

class MyStack : Stack
{
    public MyStack()
    {
        var foo = new Yandex.VpcNetwork("foo", new Yandex.VpcNetworkArgs
        {
        });
        var zone1 = new Yandex.DnsZone("zone1", new Yandex.DnsZoneArgs
        {
            Description = "desc",
            Labels = 
            {
                { "label1", "label-1-value" },
            },
            Zone = "example.com.",
            Public = false,
            PrivateNetworks = 
            {
                foo.Id,
            },
        });
        var rs1 = new Yandex.DnsRecordSet("rs1", new Yandex.DnsRecordSetArgs
        {
            ZoneId = zone1.Id,
            Type = "A",
            Ttl = 200,
            Datas = 
            {
                "10.1.0.1",
            },
        });
        var rs2 = new Yandex.DnsRecordSet("rs2", new Yandex.DnsRecordSetArgs
        {
            ZoneId = zone1.Id,
            Type = "A",
            Ttl = 200,
            Datas = 
            {
                "10.1.0.2",
            },
        });
    }

}
```


{{< /example >}}


{{< example go >}}

```go
package main

import (
	"github.com/pulumi/pulumi-yandex/sdk/go/yandex"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		foo, err := yandex.NewVpcNetwork(ctx, "foo", nil)
		if err != nil {
			return err
		}
		zone1, err := yandex.NewDnsZone(ctx, "zone1", &yandex.DnsZoneArgs{
			Description: pulumi.String("desc"),
			Labels: pulumi.StringMap{
				"label1": pulumi.String("label-1-value"),
			},
			Zone:   pulumi.String("example.com."),
			Public: pulumi.Bool(false),
			PrivateNetworks: pulumi.StringArray{
				foo.ID(),
			},
		})
		if err != nil {
			return err
		}
		_, err = yandex.NewDnsRecordSet(ctx, "rs1", &yandex.DnsRecordSetArgs{
			ZoneId: zone1.ID(),
			Type:   pulumi.String("A"),
			Ttl:    pulumi.Int(200),
			Datas: pulumi.StringArray{
				pulumi.String("10.1.0.1"),
			},
		})
		if err != nil {
			return err
		}
		_, err = yandex.NewDnsRecordSet(ctx, "rs2", &yandex.DnsRecordSetArgs{
			ZoneId: zone1.ID(),
			Type:   pulumi.String("A"),
			Ttl:    pulumi.Int(200),
			Datas: pulumi.StringArray{
				pulumi.String("10.1.0.2"),
			},
		})
		if err != nil {
			return err
		}
		return nil
	})
}
```


{{< /example >}}


{{< example python >}}

```python
import pulumi
import pulumi_yandex as yandex

foo = yandex.VpcNetwork("foo")
zone1 = yandex.DnsZone("zone1",
    description="desc",
    labels={
        "label1": "label-1-value",
    },
    zone="example.com.",
    public=False,
    private_networks=[foo.id])
rs1 = yandex.DnsRecordSet("rs1",
    zone_id=zone1.id,
    type="A",
    ttl=200,
    datas=["10.1.0.1"])
rs2 = yandex.DnsRecordSet("rs2",
    zone_id=zone1.id,
    type="A",
    ttl=200,
    datas=["10.1.0.2"])
```


{{< /example >}}


{{< example typescript >}}


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as yandex from "@pulumi/yandex";

const foo = new yandex.VpcNetwork("foo", {});
const zone1 = new yandex.DnsZone("zone1", {
    description: "desc",
    labels: {
        label1: "label-1-value",
    },
    zone: "example.com.",
    "public": false,
    privateNetworks: [foo.id],
});
const rs1 = new yandex.DnsRecordSet("rs1", {
    zoneId: zone1.id,
    type: "A",
    ttl: 200,
    datas: ["10.1.0.1"],
});
const rs2 = new yandex.DnsRecordSet("rs2", {
    zoneId: zone1.id,
    type: "A",
    ttl: 200,
    datas: ["10.1.0.2"],
});
```


{{< /example >}}





{{% /examples %}}




## Create a DnsRecordSet Resource {#create}
{{< chooser language "typescript,python,go,csharp" / >}}


{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx">DnsRecordSet</span><span class="p">(</span><span class="nx">name</span><span class="p">:</span> <span class="nx">string</span><span class="p">,</span> <span class="nx">args</span><span class="p">:</span> <span class="nx"><a href="#inputs">DnsRecordSetArgs</a></span><span class="p">,</span> <span class="nx">opts</span><span class="p">?:</span> <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class=nd>@overload</span>
<span class="k">def </span><span class="nx">DnsRecordSet</span><span class="p">(</span><span class="nx">resource_name</span><span class="p">:</span> <span class="nx">str</span><span class="p">,</span>
                 <span class="nx">opts</span><span class="p">:</span> <span class="nx"><a href="/docs/reference/pkg/python/pulumi/#pulumi.ResourceOptions">Optional[ResourceOptions]</a></span> = None<span class="p">,</span>
                 <span class="nx">datas</span><span class="p">:</span> <span class="nx">Optional[Sequence[str]]</span> = None<span class="p">,</span>
                 <span class="nx">name</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
                 <span class="nx">ttl</span><span class="p">:</span> <span class="nx">Optional[int]</span> = None<span class="p">,</span>
                 <span class="nx">type</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
                 <span class="nx">zone_id</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">)</span>
<span class=nd>@overload</span>
<span class="k">def </span><span class="nx">DnsRecordSet</span><span class="p">(</span><span class="nx">resource_name</span><span class="p">:</span> <span class="nx">str</span><span class="p">,</span>
                 <span class="nx">args</span><span class="p">:</span> <span class="nx"><a href="#inputs">DnsRecordSetArgs</a></span><span class="p">,</span>
                 <span class="nx">opts</span><span class="p">:</span> <span class="nx"><a href="/docs/reference/pkg/python/pulumi/#pulumi.ResourceOptions">Optional[ResourceOptions]</a></span> = None<span class="p">)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span><span class="nx">NewDnsRecordSet</span><span class="p">(</span><span class="nx">ctx</span><span class="p"> *</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#Context">Context</a></span><span class="p">,</span> <span class="nx">name</span><span class="p"> </span><span class="nx">string</span><span class="p">,</span> <span class="nx">args</span><span class="p"> </span><span class="nx"><a href="#inputs">DnsRecordSetArgs</a></span><span class="p">,</span> <span class="nx">opts</span><span class="p"> ...</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx">DnsRecordSet</span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx">DnsRecordSet</span><span class="p">(</span><span class="nx">string</span><span class="p"> </span><span class="nx">name<span class="p">,</span> <span class="nx"><a href="#inputs">DnsRecordSetArgs</a></span><span class="p"> </span><span class="nx">args<span class="p">,</span> <span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span><span class="p">? </span><span class="nx">opts = null<span class="p">)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language nodejs %}}

<dl class="resources-properties"><dt
        class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>The unique name of the resource.</dd><dt
        class="property-required" title="Required">
        <span>args</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inputs">DnsRecordSetArgs</a></span>
    </dt>
    <dd>The arguments to resource properties.</dd><dt
        class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span>
    </dt>
    <dd>Bag of options to control resource&#39;s behavior.</dd></dl>

{{% /choosable %}}

{{% choosable language python %}}

<dl class="resources-properties"><dt
        class="property-required" title="Required">
        <span>resource_name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>The unique name of the resource.</dd><dt
        class="property-required" title="Required">
        <span>args</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inputs">DnsRecordSetArgs</a></span>
    </dt>
    <dd>The arguments to resource properties.</dd><dt
        class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="/docs/reference/pkg/python/pulumi/#pulumi.ResourceOptions">ResourceOptions</a></span>
    </dt>
    <dd>Bag of options to control resource&#39;s behavior.</dd></dl>

{{% /choosable %}}

{{% choosable language go %}}

<dl class="resources-properties"><dt
        class="property-optional" title="Optional">
        <span>ctx</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#Context">Context</a></span>
    </dt>
    <dd>Context object for the current deployment.</dd><dt
        class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>The unique name of the resource.</dd><dt
        class="property-required" title="Required">
        <span>args</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inputs">DnsRecordSetArgs</a></span>
    </dt>
    <dd>The arguments to resource properties.</dd><dt
        class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span>
    </dt>
    <dd>Bag of options to control resource&#39;s behavior.</dd></dl>

{{% /choosable %}}

{{% choosable language csharp %}}

<dl class="resources-properties"><dt
        class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>The unique name of the resource.</dd><dt
        class="property-required" title="Required">
        <span>args</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inputs">DnsRecordSetArgs</a></span>
    </dt>
    <dd>The arguments to resource properties.</dd><dt
        class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>
    </dt>
    <dd>Bag of options to control resource&#39;s behavior.</dd></dl>

{{% /choosable %}}

## DnsRecordSet Resource Properties {#properties}

To learn more about resource properties and how to use them, see [Inputs and Outputs]({{< relref "/docs/intro/concepts/inputs-outputs" >}}) in the Architecture and Concepts docs.

### Inputs

The DnsRecordSet resource accepts the following [input]({{< relref "/docs/intro/concepts/inputs-outputs" >}}) properties:



{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="datas_csharp">
<a href="#datas_csharp" style="color: inherit; text-decoration: inherit;">Datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">List&lt;string&gt;</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="ttl_csharp">
<a href="#ttl_csharp" style="color: inherit; text-decoration: inherit;">Ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="type_csharp">
<a href="#type_csharp" style="color: inherit; text-decoration: inherit;">Type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="zoneid_csharp">
<a href="#zoneid_csharp" style="color: inherit; text-decoration: inherit;">Zone<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="name_csharp">
<a href="#name_csharp" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="datas_go">
<a href="#datas_go" style="color: inherit; text-decoration: inherit;">Datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="ttl_go">
<a href="#ttl_go" style="color: inherit; text-decoration: inherit;">Ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="type_go">
<a href="#type_go" style="color: inherit; text-decoration: inherit;">Type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="zoneid_go">
<a href="#zoneid_go" style="color: inherit; text-decoration: inherit;">Zone<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="name_go">
<a href="#name_go" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="datas_nodejs">
<a href="#datas_nodejs" style="color: inherit; text-decoration: inherit;">datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="ttl_nodejs">
<a href="#ttl_nodejs" style="color: inherit; text-decoration: inherit;">ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="type_nodejs">
<a href="#type_nodejs" style="color: inherit; text-decoration: inherit;">type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="zoneid_nodejs">
<a href="#zoneid_nodejs" style="color: inherit; text-decoration: inherit;">zone<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="name_nodejs">
<a href="#name_nodejs" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-required"
            title="Required">
        <span id="datas_python">
<a href="#datas_python" style="color: inherit; text-decoration: inherit;">datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">Sequence[str]</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="ttl_python">
<a href="#ttl_python" style="color: inherit; text-decoration: inherit;">ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="type_python">
<a href="#type_python" style="color: inherit; text-decoration: inherit;">type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-required"
            title="Required">
        <span id="zone_id_python">
<a href="#zone_id_python" style="color: inherit; text-decoration: inherit;">zone_<wbr>id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="name_python">
<a href="#name_python" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd></dl>
{{% /choosable %}}


### Outputs

All [input](#inputs) properties are implicitly available as output properties. Additionally, the DnsRecordSet resource produces the following output properties:



{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_csharp">
<a href="#id_csharp" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_go">
<a href="#id_go" style="color: inherit; text-decoration: inherit;">Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_nodejs">
<a href="#id_nodejs" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-"
            title="">
        <span id="id_python">
<a href="#id_python" style="color: inherit; text-decoration: inherit;">id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The provider-assigned unique ID for this managed resource.{{% /md %}}</dd></dl>
{{% /choosable %}}



## Look up an Existing DnsRecordSet Resource {#look-up}

Get an existing DnsRecordSet resource's state with the given name, ID, and optional extra properties used to qualify the lookup.
{{< chooser language "typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span><span class="p">:</span> <span class="nx">string</span><span class="p">,</span> <span class="nx">id</span><span class="p">:</span> <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">Input&lt;ID&gt;</a></span><span class="p">,</span> <span class="nx">state</span><span class="p">?:</span> <span class="nx">DnsRecordSetState</span><span class="p">,</span> <span class="nx">opts</span><span class="p">?:</span> <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">): </span><span class="nx">DnsRecordSet</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class=nd>@staticmethod</span>
<span class="k">def </span><span class="nf">get</span><span class="p">(</span><span class="nx">resource_name</span><span class="p">:</span> <span class="nx">str</span><span class="p">,</span>
        <span class="nx">id</span><span class="p">:</span> <span class="nx">str</span><span class="p">,</span>
        <span class="nx">opts</span><span class="p">:</span> <span class="nx"><a href="/docs/reference/pkg/python/pulumi/#pulumi.ResourceOptions">Optional[ResourceOptions]</a></span> = None<span class="p">,</span>
        <span class="nx">datas</span><span class="p">:</span> <span class="nx">Optional[Sequence[str]]</span> = None<span class="p">,</span>
        <span class="nx">name</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
        <span class="nx">ttl</span><span class="p">:</span> <span class="nx">Optional[int]</span> = None<span class="p">,</span>
        <span class="nx">type</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">,</span>
        <span class="nx">zone_id</span><span class="p">:</span> <span class="nx">Optional[str]</span> = None<span class="p">) -&gt;</span> DnsRecordSet</code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetDnsRecordSet<span class="p">(</span><span class="nx">ctx</span><span class="p"> *</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#Context">Context</a></span><span class="p">,</span> <span class="nx">name</span><span class="p"> </span><span class="nx">string</span><span class="p">,</span> <span class="nx">id</span><span class="p"> </span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#IDInput">IDInput</a></span><span class="p">,</span> <span class="nx">state</span><span class="p"> *</span><span class="nx">DnsRecordSetState</span><span class="p">,</span> <span class="nx">opts</span><span class="p"> ...</span><span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v3/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx">DnsRecordSet</span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx">DnsRecordSet</span><span class="nf"> Get</span><span class="p">(</span><span class="nx">string</span><span class="p"> </span><span class="nx">name<span class="p">,</span> <span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input-1.html">Input&lt;string&gt;</a></span><span class="p"> </span><span class="nx">id<span class="p">,</span> <span class="nx">DnsRecordSetState</span><span class="p">? </span><span class="nx">state<span class="p">,</span> <span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span><span class="p">? </span><span class="nx">opts = null<span class="p">)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language nodejs %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>resource_name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
</dl>
{{% /choosable %}}

{{% choosable language go %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language csharp %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

The following state arguments are supported:


{{% choosable language csharp %}}
<dl class="resources-properties"><dt class="property-optional"
            title="Optional">
        <span id="state_datas_csharp">
<a href="#state_datas_csharp" style="color: inherit; text-decoration: inherit;">Datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">List&lt;string&gt;</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_name_csharp">
<a href="#state_name_csharp" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_ttl_csharp">
<a href="#state_ttl_csharp" style="color: inherit; text-decoration: inherit;">Ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_type_csharp">
<a href="#state_type_csharp" style="color: inherit; text-decoration: inherit;">Type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_zoneid_csharp">
<a href="#state_zoneid_csharp" style="color: inherit; text-decoration: inherit;">Zone<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language go %}}
<dl class="resources-properties"><dt class="property-optional"
            title="Optional">
        <span id="state_datas_go">
<a href="#state_datas_go" style="color: inherit; text-decoration: inherit;">Datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_name_go">
<a href="#state_name_go" style="color: inherit; text-decoration: inherit;">Name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_ttl_go">
<a href="#state_ttl_go" style="color: inherit; text-decoration: inherit;">Ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_type_go">
<a href="#state_type_go" style="color: inherit; text-decoration: inherit;">Type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_zoneid_go">
<a href="#state_zoneid_go" style="color: inherit; text-decoration: inherit;">Zone<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language nodejs %}}
<dl class="resources-properties"><dt class="property-optional"
            title="Optional">
        <span id="state_datas_nodejs">
<a href="#state_datas_nodejs" style="color: inherit; text-decoration: inherit;">datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_name_nodejs">
<a href="#state_name_nodejs" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_ttl_nodejs">
<a href="#state_ttl_nodejs" style="color: inherit; text-decoration: inherit;">ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_type_nodejs">
<a href="#state_type_nodejs" style="color: inherit; text-decoration: inherit;">type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_zoneid_nodejs">
<a href="#state_zoneid_nodejs" style="color: inherit; text-decoration: inherit;">zone<wbr>Id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd></dl>
{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties"><dt class="property-optional"
            title="Optional">
        <span id="state_datas_python">
<a href="#state_datas_python" style="color: inherit; text-decoration: inherit;">datas</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">Sequence[str]</span>
    </dt>
    <dd>{{% md %}}The string data for the records in this record set.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_name_python">
<a href="#state_name_python" style="color: inherit; text-decoration: inherit;">name</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The DNS name this record set will apply to.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_ttl_python">
<a href="#state_ttl_python" style="color: inherit; text-decoration: inherit;">ttl</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The time-to-live of this record set (seconds).
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_type_python">
<a href="#state_type_python" style="color: inherit; text-decoration: inherit;">type</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The DNS record set type.
{{% /md %}}</dd><dt class="property-optional"
            title="Optional">
        <span id="state_zone_id_python">
<a href="#state_zone_id_python" style="color: inherit; text-decoration: inherit;">zone_<wbr>id</a>
</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the zone in which this record set will reside.
{{% /md %}}</dd></dl>
{{% /choosable %}}





## Import


DNS recordset can be imported using this format

```sh
 $ pulumi import yandex:index/dnsRecordSet:DnsRecordSet rs1 {{zone_id}}/{{name}}/{{type}}
```




<h2 id="package-details">Package Details</h2>
<dl class="package-details">
	<dt>Repository</dt>
	<dd><a href="https://github.com/pulumi/pulumi-yandex">https://github.com/pulumi/pulumi-yandex</a></dd>
	<dt>License</dt>
	<dd>Apache-2.0</dd>
	<dt>Notes</dt>
	<dd>{{% md %}}This Pulumi package is based on the [`yandex` Terraform Provider](https://github.com/yandex-cloud/terraform-provider-yandex).{{% /md %}}</dd>
</dl>

