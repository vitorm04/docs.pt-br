---
title: '&lt;comutadores&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: ed5d30408b2c0f45f3bef091f4828bd812a63a7a
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083347"
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="69e2f-102">&lt;comutadores&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="69e2f-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="69e2f-103">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="69e2f-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="69e2f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="69e2f-104">\<configuration></span></span>  
<span data-ttu-id="69e2f-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="69e2f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="69e2f-106">\<switches></span><span class="sxs-lookup"><span data-stu-id="69e2f-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e2f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69e2f-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69e2f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="69e2f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="69e2f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="69e2f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69e2f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="69e2f-110">Attributes</span></span>  
 <span data-ttu-id="69e2f-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="69e2f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69e2f-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="69e2f-112">Child Elements</span></span>  
  
|<span data-ttu-id="69e2f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="69e2f-113">Element</span></span>|<span data-ttu-id="69e2f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="69e2f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69e2f-115">\<add></span><span class="sxs-lookup"><span data-stu-id="69e2f-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="69e2f-116">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="69e2f-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69e2f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="69e2f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="69e2f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="69e2f-118">Element</span></span>|<span data-ttu-id="69e2f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="69e2f-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="69e2f-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69e2f-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="69e2f-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="69e2f-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69e2f-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="69e2f-122">Remarks</span></span>  
 <span data-ttu-id="69e2f-123">Você pode alterar o nível de uma opção de rastreamento, colocando-o em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="69e2f-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="69e2f-124">Se a opção é um <xref:System.Diagnostics.BooleanSwitch>, você pode ativar e desativar.</span><span class="sxs-lookup"><span data-stu-id="69e2f-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="69e2f-125">Se a opção é um <xref:System.Diagnostics.TraceSwitch>, você pode atribuir diferentes níveis a ele para especificar os tipos de rastreamento ou depuração mensagens as saídas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69e2f-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e2f-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69e2f-126">Example</span></span>  
 <span data-ttu-id="69e2f-127">O exemplo a seguir mostra como usar o  **\<alternar >** elemento para definir a `General` opção de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar o `Data` opção de rastreamento Boolean.</span><span class="sxs-lookup"><span data-stu-id="69e2f-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69e2f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69e2f-128">See also</span></span>
- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="69e2f-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="69e2f-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
