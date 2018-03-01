---
title: '&lt;Adicionar&gt; elemento para &lt;switches&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 4406caa4da1375bea9809843ca96774e24421d5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="f85c0-102">&lt;Adicionar&gt; elemento para &lt;switches&gt;</span><span class="sxs-lookup"><span data-stu-id="f85c0-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="f85c0-103">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="f85c0-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="f85c0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f85c0-104">\<configuration></span></span>  
<span data-ttu-id="f85c0-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="f85c0-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f85c0-106">\<Switches ></span><span class="sxs-lookup"><span data-stu-id="f85c0-106">\<switches></span></span>  
<span data-ttu-id="f85c0-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f85c0-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f85c0-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f85c0-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f85c0-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f85c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f85c0-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f85c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f85c0-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f85c0-111">Attributes</span></span>  
  
|<span data-ttu-id="f85c0-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f85c0-112">Attribute</span></span>|<span data-ttu-id="f85c0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f85c0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f85c0-114">**name**</span><span class="sxs-lookup"><span data-stu-id="f85c0-114">**name**</span></span>|<span data-ttu-id="f85c0-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f85c0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="f85c0-116">Especifica o nome do comutador.</span><span class="sxs-lookup"><span data-stu-id="f85c0-116">Specifies the name of the switch.</span></span> <span data-ttu-id="f85c0-117">O valor deste atributo corresponde do *displayName* parâmetro que é passado para a opção construtor.</span><span class="sxs-lookup"><span data-stu-id="f85c0-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="f85c0-118">**value**</span><span class="sxs-lookup"><span data-stu-id="f85c0-118">**value**</span></span>|<span data-ttu-id="f85c0-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f85c0-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="f85c0-120">Especifica o nível do comutador.</span><span class="sxs-lookup"><span data-stu-id="f85c0-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f85c0-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f85c0-121">Child Elements</span></span>  
 <span data-ttu-id="f85c0-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f85c0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f85c0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f85c0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f85c0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f85c0-124">Element</span></span>|<span data-ttu-id="f85c0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f85c0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f85c0-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f85c0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="f85c0-127">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="f85c0-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f85c0-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="f85c0-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f85c0-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="f85c0-129">Remarks</span></span>  
 <span data-ttu-id="f85c0-130">Você pode alterar o nível de um comutador de rastreamento, colocando-o em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f85c0-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="f85c0-131">Se a opção é uma <xref:System.Diagnostics.BooleanSwitch>, você pode ativar e desativar.</span><span class="sxs-lookup"><span data-stu-id="f85c0-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="f85c0-132">Se a opção é uma <xref:System.Diagnostics.TraceSwitch>, você pode atribuir diferentes níveis-o para especificar os tipos de rastreamento ou as saídas de aplicativo de mensagens de depuração.</span><span class="sxs-lookup"><span data-stu-id="f85c0-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f85c0-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f85c0-133">Example</span></span>  
 <span data-ttu-id="f85c0-134">O exemplo a seguir mostra como usar o  **\<Adicionar >** elemento para definir o `General` alternar de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar o `Data` opção trace Boolean.</span><span class="sxs-lookup"><span data-stu-id="f85c0-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f85c0-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f85c0-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="f85c0-136">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f85c0-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
