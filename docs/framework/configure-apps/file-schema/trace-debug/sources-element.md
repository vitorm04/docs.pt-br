---
title: '&lt;fontes&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 73fe0fb13c191843516a2218c708851abc1851b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752696"
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="40b90-102">&lt;fontes&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="40b90-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="40b90-103">Especifica as fontes de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="40b90-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="40b90-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="40b90-104">\<configuration></span></span>  
<span data-ttu-id="40b90-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="40b90-105">\<system.diagnostics></span></span>  
<span data-ttu-id="40b90-106">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="40b90-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b90-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40b90-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40b90-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="40b90-108">Attributes and Elements</span></span>  
 <span data-ttu-id="40b90-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="40b90-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40b90-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="40b90-110">Attributes</span></span>  
 <span data-ttu-id="40b90-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="40b90-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40b90-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="40b90-112">Child Elements</span></span>  
  
|<span data-ttu-id="40b90-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="40b90-113">Element</span></span>|<span data-ttu-id="40b90-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="40b90-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40b90-115">\<source></span><span class="sxs-lookup"><span data-stu-id="40b90-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="40b90-116">Elemento obrigatório.</span><span class="sxs-lookup"><span data-stu-id="40b90-116">Required element.</span></span><br /><br /> <span data-ttu-id="40b90-117">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="40b90-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40b90-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="40b90-118">Parent Elements</span></span>  
  
|<span data-ttu-id="40b90-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="40b90-119">Element</span></span>|<span data-ttu-id="40b90-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="40b90-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="40b90-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40b90-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="40b90-122">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="40b90-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40b90-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="40b90-123">Remarks</span></span>  
 <span data-ttu-id="40b90-124">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40b90-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40b90-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40b90-125">Example</span></span>  
 <span data-ttu-id="40b90-126">O exemplo a seguir mostra como usar o `<sources>` elemento a ser adicionado a origem de rastreamento `mySource` e definir o nível para a alternância de origem nomeado `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="40b90-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="40b90-127">Um ouvinte de rastreamento do console é adicionado, que grava informações de rastreamento para o console.</span><span class="sxs-lookup"><span data-stu-id="40b90-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"   
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"   
                     initializeData="Error" />  
               </add>  
               <remove name="Default" />  
            </listeners>  
         </source>  
      </sources>  
      <switches>  
         <add name="sourceSwitch" value="Warning" />  
      </switches>    
   </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40b90-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40b90-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="40b90-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="40b90-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="40b90-130">\<source></span><span class="sxs-lookup"><span data-stu-id="40b90-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
