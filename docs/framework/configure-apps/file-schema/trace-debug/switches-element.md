---
title: Elemento <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153224"
---
# <a name="switches-element"></a><span data-ttu-id="61dce-102">\<switches elemento></span><span class="sxs-lookup"><span data-stu-id="61dce-102">\<switches> Element</span></span>
<span data-ttu-id="61dce-103">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="61dce-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="61dce-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="61dce-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="61dce-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="61dce-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="61dce-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<interruptores>**</span><span class="sxs-lookup"><span data-stu-id="61dce-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="61dce-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61dce-107">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61dce-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="61dce-108">Attributes and Elements</span></span>  
 <span data-ttu-id="61dce-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="61dce-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61dce-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="61dce-110">Attributes</span></span>  
 <span data-ttu-id="61dce-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="61dce-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="61dce-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="61dce-112">Child Elements</span></span>  
  
|<span data-ttu-id="61dce-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="61dce-113">Element</span></span>|<span data-ttu-id="61dce-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="61dce-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61dce-115">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="61dce-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="61dce-116">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="61dce-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61dce-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="61dce-117">Parent Elements</span></span>  
  
|<span data-ttu-id="61dce-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="61dce-118">Element</span></span>|<span data-ttu-id="61dce-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="61dce-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="61dce-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61dce-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="61dce-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="61dce-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61dce-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="61dce-122">Remarks</span></span>  
 <span data-ttu-id="61dce-123">Você pode alterar o nível de um switch de rastreamento colocando-o em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="61dce-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="61dce-124">Se o interruptor <xref:System.Diagnostics.BooleanSwitch>for um, você pode ligá-lo e desatificar.</span><span class="sxs-lookup"><span data-stu-id="61dce-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="61dce-125">Se o switch <xref:System.Diagnostics.TraceSwitch>for um , você pode atribuir diferentes níveis a ele para especificar os tipos de mensagens de rastreamento ou depuração das saídas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61dce-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61dce-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61dce-126">Example</span></span>  
 <span data-ttu-id="61dce-127">O exemplo a seguir \*\* \<\*\* mostra como usar `General` o elemento switch>para definir o switch de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e ativar o `Data` switch de rastreamento booleano.</span><span class="sxs-lookup"><span data-stu-id="61dce-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61dce-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="61dce-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="61dce-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="61dce-129">Trace and Debug Settings Schema</span></span>](index.md)
