---
title: Elemento <sources>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 2a76816ee73f516b3c7544877a77531acaa8e09c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153263"
---
# <a name="sources-element"></a><span data-ttu-id="c5943-102">\<fontes> Elemento</span><span class="sxs-lookup"><span data-stu-id="c5943-102">\<sources> Element</span></span>
<span data-ttu-id="c5943-103">Especifica fontes de rastreamento que iniciam o rastreamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c5943-103">Specifies trace sources that initiate tracing messages.</span></span>  

<span data-ttu-id="c5943-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5943-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5943-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5943-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="c5943-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<fontes>**</span><span class="sxs-lookup"><span data-stu-id="c5943-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c5943-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5943-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5943-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5943-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c5943-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c5943-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5943-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5943-110">Attributes</span></span>  
 <span data-ttu-id="c5943-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c5943-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5943-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5943-112">Child Elements</span></span>  
  
|<span data-ttu-id="c5943-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5943-113">Element</span></span>|<span data-ttu-id="c5943-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5943-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5943-115">\<>fonte</span><span class="sxs-lookup"><span data-stu-id="c5943-115">\<source></span></span>](source-element.md)|<span data-ttu-id="c5943-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="c5943-116">Required element.</span></span><br /><br /> <span data-ttu-id="c5943-117">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c5943-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5943-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5943-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c5943-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5943-119">Element</span></span>|<span data-ttu-id="c5943-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5943-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c5943-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5943-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c5943-122">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="c5943-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5943-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5943-123">Remarks</span></span>  
 <span data-ttu-id="c5943-124">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5943-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5943-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5943-125">Example</span></span>  
 <span data-ttu-id="c5943-126">O exemplo a seguir `<sources>` mostra como usar `mySource` o elemento para adicionar a `sourceSwitch`fonte de rastreamento e definir o nível para o switch de origem chamado .</span><span class="sxs-lookup"><span data-stu-id="c5943-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="c5943-127">Um ouvinte de rastreamento de console é adicionado que grava informações de rastreamento para o console.</span><span class="sxs-lookup"><span data-stu-id="c5943-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5943-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5943-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="c5943-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="c5943-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c5943-130">\<>fonte</span><span class="sxs-lookup"><span data-stu-id="c5943-130">\<source></span></span>](source-element.md)
