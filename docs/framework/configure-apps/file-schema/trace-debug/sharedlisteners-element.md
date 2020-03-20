---
title: Elemento <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153315"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="dd8cf-102">\<compartilhadoOuvintes> Elemento</span><span class="sxs-lookup"><span data-stu-id="dd8cf-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="dd8cf-103">Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="dd8cf-104">Esses ouvintes não recebem nenhum vestígio por padrão, e não é possível recuperar esses ouvintes em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="dd8cf-105">Os ouvintes identificados como ouvintes compartilhados podem ser adicionados a fontes ou vestígios pelo nome.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="dd8cf-106">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="dd8cf-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="dd8cf-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd8cf-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="dd8cf-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<>de ouvintes compartilhados**</span><span class="sxs-lookup"><span data-stu-id="dd8cf-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd8cf-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd8cf-109">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd8cf-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd8cf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd8cf-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd8cf-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd8cf-112">Attributes</span></span>  
 <span data-ttu-id="dd8cf-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd8cf-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd8cf-114">Child Elements</span></span>  
  
|<span data-ttu-id="dd8cf-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd8cf-115">Element</span></span>|<span data-ttu-id="dd8cf-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd8cf-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd8cf-117">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="dd8cf-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="dd8cf-118">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd8cf-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd8cf-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dd8cf-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd8cf-120">Element</span></span>|<span data-ttu-id="dd8cf-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd8cf-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="dd8cf-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="dd8cf-123">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd8cf-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd8cf-124">Remarks</span></span>  
 <span data-ttu-id="dd8cf-125">Adicionar um ouvinte à coleção de ouvintes compartilhados não o torna um ouvinte ativo.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="dd8cf-126">Ele ainda deve ser adicionado a uma fonte de `Listeners` rastreamento ou um traço adicionando-o à coleção para esse elemento de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="dd8cf-127">As classes de ouvinte no Quadro <xref:System.Diagnostics.TraceListener> .NET derivam da classe.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="dd8cf-128">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd8cf-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd8cf-129">Example</span></span>  
 <span data-ttu-id="dd8cf-130">O exemplo a seguir `<sharedListeners>` mostra como usar `console` o `Listeners` elemento para <xref:System.Diagnostics.TraceSource> adicionar <xref:System.Diagnostics.Trace> o ouvinte à coleção para as classes e classes.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="dd8cf-131">O ouvinte de rastreamento do console grava informações <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace>de rastreamento para o console através de chamadas para ou .</span><span class="sxs-lookup"><span data-stu-id="dd8cf-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="dd8cf-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd8cf-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="dd8cf-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="dd8cf-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dd8cf-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="dd8cf-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
