---
title: Elemento <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: b7144b0a7004ba32b21cbc98513df574a5a9e1d9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195175"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="3c37c-102">Elemento \<listeners> para \<source></span><span class="sxs-lookup"><span data-stu-id="3c37c-102">\<listeners> Element for \<source></span></span>

<span data-ttu-id="3c37c-103">Adiciona ou remove ouvintes na <xref:System.Diagnostics.TraceSource.Listeners%2A> coleção para um <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="3c37c-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="3c37c-104">Um ouvinte direciona a saída de rastreamento para um destino apropriado, como um log, uma janela ou um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="3c37c-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="3c37c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c37c-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c37c-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3c37c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3c37c-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3c37c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c37c-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3c37c-108">Attributes</span></span>  

 <span data-ttu-id="3c37c-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3c37c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c37c-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3c37c-110">Child Elements</span></span>  
  
|<span data-ttu-id="3c37c-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c37c-111">Element</span></span>|<span data-ttu-id="3c37c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c37c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="3c37c-113">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="3c37c-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="3c37c-114">Remove um ouvinte da `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="3c37c-114">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="3c37c-115">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3c37c-115">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c37c-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3c37c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3c37c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c37c-117">Element</span></span>|<span data-ttu-id="3c37c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c37c-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3c37c-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c37c-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3c37c-120">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="3c37c-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="3c37c-121">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3c37c-121">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="3c37c-122">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3c37c-122">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c37c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c37c-123">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3c37c-124">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3c37c-124">Configuration File</span></span>  

 <span data-ttu-id="3c37c-125">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c37c-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c37c-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c37c-126">Example</span></span>  

 <span data-ttu-id="3c37c-127">O exemplo a seguir mostra como usar o `<listeners>` elemento para adicionar um ouvinte de rastreamento de console à `mySource` origem e remover o ouvinte de rastreamento padrão.</span><span class="sxs-lookup"><span data-stu-id="3c37c-127">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c37c-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="3c37c-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3c37c-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="3c37c-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3c37c-130">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="3c37c-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
