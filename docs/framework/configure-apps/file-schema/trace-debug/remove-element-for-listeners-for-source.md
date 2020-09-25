---
title: <remove> Elemento para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 53ba773ea1cb31955e59c1f57e1c0cc807227402
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173867"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="de480-102">\<remove> Elemento para \<listeners> para \<source></span><span class="sxs-lookup"><span data-stu-id="de480-102">\<remove> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="de480-103">Remove um ouvinte da coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="de480-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="de480-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de480-104">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de480-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de480-105">Attributes and Elements</span></span>  

 <span data-ttu-id="de480-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="de480-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de480-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="de480-107">Attributes</span></span>  
  
|<span data-ttu-id="de480-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="de480-108">Attribute</span></span>|<span data-ttu-id="de480-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="de480-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="de480-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="de480-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="de480-111">O nome do ouvinte a ser removido da `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="de480-111">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de480-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de480-112">Child Elements</span></span>  

 <span data-ttu-id="de480-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="de480-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de480-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de480-114">Parent Elements</span></span>  
  
|<span data-ttu-id="de480-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="de480-115">Element</span></span>|<span data-ttu-id="de480-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="de480-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="de480-117">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de480-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="de480-118">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="de480-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="de480-119">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="de480-119">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="de480-120">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="de480-120">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="de480-121">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="de480-121">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de480-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="de480-122">Remarks</span></span>  

 <span data-ttu-id="de480-123">O `<remove>` elemento remove um ouvinte especificado da `Listeners` coleção para uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="de480-123">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="de480-124">Você pode remover um elemento da `Listeners` coleção para uma fonte de rastreamento programaticamente chamando o <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> método na <xref:System.Diagnostics.TraceSource.Listeners%2A> propriedade da <xref:System.Diagnostics.TraceSource> instância.</span><span class="sxs-lookup"><span data-stu-id="de480-124">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="de480-125">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de480-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de480-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de480-126">Example</span></span>  

 <span data-ttu-id="de480-127">O exemplo a seguir mostra como usar o `<remove>` elemento antes de usar o `<add>` elemento para adicionar o ouvinte `console` à `Listeners` coleção para a origem do rastreamento `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="de480-127">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="de480-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="de480-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="de480-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="de480-129">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="de480-130">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="de480-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
