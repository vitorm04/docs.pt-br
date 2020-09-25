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
ms.openlocfilehash: 670fb359f892d83feac56c849361c4b980d9a922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173803"
---
# <a name="sources-element"></a><span data-ttu-id="d298b-102">Elemento \<sources></span><span class="sxs-lookup"><span data-stu-id="d298b-102">\<sources> Element</span></span>

<span data-ttu-id="d298b-103">Especifica fontes de rastreamento que iniciam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d298b-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="d298b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d298b-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d298b-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d298b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d298b-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d298b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d298b-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d298b-107">Attributes</span></span>  

 <span data-ttu-id="d298b-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d298b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d298b-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d298b-109">Child Elements</span></span>  
  
|<span data-ttu-id="d298b-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="d298b-110">Element</span></span>|<span data-ttu-id="d298b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d298b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="d298b-112">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="d298b-112">Required element.</span></span><br /><br /> <span data-ttu-id="d298b-113">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d298b-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d298b-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d298b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d298b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d298b-115">Element</span></span>|<span data-ttu-id="d298b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d298b-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d298b-117">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d298b-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d298b-118">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="d298b-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d298b-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="d298b-119">Remarks</span></span>  

 <span data-ttu-id="d298b-120">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d298b-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d298b-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d298b-121">Example</span></span>  

 <span data-ttu-id="d298b-122">O exemplo a seguir mostra como usar o `<sources>` elemento para adicionar a origem de rastreamento `mySource` e definir o nível para a opção de origem denominada `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="d298b-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="d298b-123">Um ouvinte de rastreamento de console é adicionado que grava informações de rastreamento no console do.</span><span class="sxs-lookup"><span data-stu-id="d298b-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d298b-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="d298b-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="d298b-125">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="d298b-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
