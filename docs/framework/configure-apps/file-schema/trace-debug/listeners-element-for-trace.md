---
title: Elemento <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153367"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="7e2fc-102">\<ouvintes> \<Elemento para rastreamento></span><span class="sxs-lookup"><span data-stu-id="7e2fc-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="7e2fc-103">Especifica um ouvinte que coleta, armazena e encaminha mensagens.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="7e2fc-104">Os ouvintes direcionam a saída de rastreamento para um alvo apropriado.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="7e2fc-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e2fc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7e2fc-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e2fc-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="7e2fc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<traçar>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e2fc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="7e2fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ouvintes>**</span><span class="sxs-lookup"><span data-stu-id="7e2fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7e2fc-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e2fc-109">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e2fc-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7e2fc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7e2fc-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e2fc-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e2fc-112">Attributes</span></span>  
 <span data-ttu-id="7e2fc-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7e2fc-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7e2fc-114">Child Elements</span></span>  
  
|<span data-ttu-id="7e2fc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e2fc-115">Element</span></span>|<span data-ttu-id="7e2fc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e2fc-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e2fc-117">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="7e2fc-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="7e2fc-118">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="7e2fc-119">\<claro></span><span class="sxs-lookup"><span data-stu-id="7e2fc-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="7e2fc-120">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="7e2fc-121">\<remover></span><span class="sxs-lookup"><span data-stu-id="7e2fc-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="7e2fc-122">Remove um ouvinte da `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e2fc-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7e2fc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7e2fc-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e2fc-124">Element</span></span>|<span data-ttu-id="7e2fc-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e2fc-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7e2fc-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7e2fc-127">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="7e2fc-128">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e2fc-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e2fc-129">Remarks</span></span>  
 <span data-ttu-id="7e2fc-130">As <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> aulas compartilham a mesma coleção **de Ouvintes.**</span><span class="sxs-lookup"><span data-stu-id="7e2fc-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="7e2fc-131">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="7e2fc-132">As classes de ouvinte enviadas com o <xref:System.Diagnostics.TraceListener> Quadro .NET derivam da classe.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="7e2fc-133">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7e2fc-133">Configuration File</span></span>  
 <span data-ttu-id="7e2fc-134">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e2fc-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e2fc-135">Example</span></span>  
 <span data-ttu-id="7e2fc-136">O exemplo a seguir mostra como usar os `MyListener` `MyEventListener` \*\* \<ouvintes>\*\* elemento para adicionar os ouvintes e a coleção **ouvintes.**</span><span class="sxs-lookup"><span data-stu-id="7e2fc-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="7e2fc-137">`MyListener`cria um `MyListener.log` arquivo chamado e grava a saída para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="7e2fc-138">`MyEventListener`cria uma entrada no registro de eventos.</span><span class="sxs-lookup"><span data-stu-id="7e2fc-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e2fc-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e2fc-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="7e2fc-140">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="7e2fc-140">Trace and Debug Settings Schema</span></span>](index.md)
