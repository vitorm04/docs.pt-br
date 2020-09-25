---
title: Elemento <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 59d078f8dc573a1ce949d225f497dd4500fe808f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173855"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="5df56-102">Elemento \<listeners> para \<trace></span><span class="sxs-lookup"><span data-stu-id="5df56-102">\<listeners> Element for \<trace></span></span>

<span data-ttu-id="5df56-103">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="5df56-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="5df56-104">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="5df56-104">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="5df56-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5df56-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5df56-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5df56-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5df56-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5df56-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5df56-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="5df56-108">Attributes</span></span>  

 <span data-ttu-id="5df56-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5df56-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5df56-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5df56-110">Child Elements</span></span>  
  
|<span data-ttu-id="5df56-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="5df56-111">Element</span></span>|<span data-ttu-id="5df56-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5df56-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="5df56-113">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="5df56-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="5df56-114">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5df56-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="5df56-115">Remove um ouvinte da `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="5df56-115">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5df56-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5df56-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5df56-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5df56-117">Element</span></span>|<span data-ttu-id="5df56-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5df56-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5df56-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5df56-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5df56-120">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5df56-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="5df56-121">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5df56-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5df56-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="5df56-122">Remarks</span></span>  

 <span data-ttu-id="5df56-123">As <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes e compartilham a mesma coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="5df56-123">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="5df56-124">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="5df56-124">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="5df56-125">As classes de ouvinte fornecidas com o .NET Framework derivam da <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="5df56-125">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5df56-126">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="5df56-126">Configuration File</span></span>  

 <span data-ttu-id="5df56-127">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5df56-127">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5df56-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5df56-128">Example</span></span>  

 <span data-ttu-id="5df56-129">O exemplo a seguir mostra como usar o **\<listeners>** elemento para adicionar os ouvintes `MyListener` e a `MyEventListener` coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="5df56-129">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="5df56-130">`MyListener` Cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="5df56-130">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="5df56-131">`MyEventListener` Cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="5df56-131">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5df56-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="5df56-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="5df56-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="5df56-133">Trace and Debug Settings Schema</span></span>](index.md)
