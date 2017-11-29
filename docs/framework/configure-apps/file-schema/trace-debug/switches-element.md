---
title: '&lt;comutadores&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6240f8192f2a31faeb81528e54481eb06cc04d04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="586be-102">&lt;comutadores&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="586be-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="586be-103">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="586be-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="586be-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="586be-104">\<configuration></span></span>  
<span data-ttu-id="586be-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="586be-105">\<system.diagnostics></span></span>  
<span data-ttu-id="586be-106">\<Switches ></span><span class="sxs-lookup"><span data-stu-id="586be-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586be-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="586be-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="586be-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="586be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="586be-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="586be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="586be-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="586be-110">Attributes</span></span>  
 <span data-ttu-id="586be-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="586be-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="586be-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="586be-112">Child Elements</span></span>  
  
|<span data-ttu-id="586be-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="586be-113">Element</span></span>|<span data-ttu-id="586be-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="586be-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="586be-115">\<add></span><span class="sxs-lookup"><span data-stu-id="586be-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="586be-116">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="586be-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="586be-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="586be-117">Parent Elements</span></span>  
  
|<span data-ttu-id="586be-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="586be-118">Element</span></span>|<span data-ttu-id="586be-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="586be-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="586be-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="586be-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="586be-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="586be-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="586be-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="586be-122">Remarks</span></span>  
 <span data-ttu-id="586be-123">Você pode alterar o nível de um comutador de rastreamento, colocando-o em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="586be-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="586be-124">Se a opção é uma <xref:System.Diagnostics.BooleanSwitch>, você pode ativar e desativar.</span><span class="sxs-lookup"><span data-stu-id="586be-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="586be-125">Se a opção é uma <xref:System.Diagnostics.TraceSwitch>, você pode atribuir diferentes níveis-o para especificar os tipos de rastreamento ou as saídas de aplicativo de mensagens de depuração.</span><span class="sxs-lookup"><span data-stu-id="586be-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="586be-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="586be-126">Example</span></span>  
 <span data-ttu-id="586be-127">O exemplo a seguir mostra como usar o  **\<alternar >** elemento para definir o `General` alternar de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar o `Data` opção trace Boolean.</span><span class="sxs-lookup"><span data-stu-id="586be-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="586be-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="586be-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="586be-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="586be-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
