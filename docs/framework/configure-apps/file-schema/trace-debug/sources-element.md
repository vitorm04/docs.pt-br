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
ms.openlocfilehash: 0ca35d9be5e1eaf36a2c9cae99efc2736ef3403d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699203"
---
# <a name="sources-element"></a><span data-ttu-id="b1039-102">\<sources > elemento</span><span class="sxs-lookup"><span data-stu-id="b1039-102">\<sources> Element</span></span>
<span data-ttu-id="b1039-103">Especifica fontes de rastreamento que iniciam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b1039-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
[<span data-ttu-id="b1039-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="b1039-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b1039-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1039-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="b1039-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<sources >**</span><span class="sxs-lookup"><span data-stu-id="b1039-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1039-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1039-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1039-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1039-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1039-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1039-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1039-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1039-110">Attributes</span></span>  
 <span data-ttu-id="b1039-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b1039-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1039-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1039-112">Child Elements</span></span>  
  
|<span data-ttu-id="b1039-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1039-113">Element</span></span>|<span data-ttu-id="b1039-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1039-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1039-115">\<source></span><span class="sxs-lookup"><span data-stu-id="b1039-115">\<source></span></span>](source-element.md)|<span data-ttu-id="b1039-116">Elemento obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b1039-116">Required element.</span></span><br /><br /> <span data-ttu-id="b1039-117">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b1039-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1039-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1039-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b1039-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1039-119">Element</span></span>|<span data-ttu-id="b1039-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1039-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b1039-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1039-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b1039-122">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="b1039-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1039-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1039-123">Remarks</span></span>  
 <span data-ttu-id="b1039-124">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1039-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1039-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1039-125">Example</span></span>  
 <span data-ttu-id="b1039-126">O exemplo a seguir mostra como usar o elemento `<sources>` para adicionar a fonte de rastreamento `mySource` e definir o nível para a opção de origem denominada `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="b1039-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="b1039-127">Um ouvinte de rastreamento de console é adicionado que grava informações de rastreamento no console do.</span><span class="sxs-lookup"><span data-stu-id="b1039-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1039-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1039-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="b1039-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="b1039-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b1039-130">\<source></span><span class="sxs-lookup"><span data-stu-id="b1039-130">\<source></span></span>](source-element.md)
