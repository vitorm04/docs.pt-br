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
ms.openlocfilehash: 92a1c8db43579048945d76082e3ebd2862efd7ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920439"
---
# <a name="switches-element"></a><span data-ttu-id="84609-102">\<alterna > elemento</span><span class="sxs-lookup"><span data-stu-id="84609-102">\<switches> Element</span></span>
<span data-ttu-id="84609-103">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="84609-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="84609-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="84609-104">\<configuration></span></span>  
<span data-ttu-id="84609-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="84609-105">\<system.diagnostics></span></span>  
<span data-ttu-id="84609-106">\<alterna ></span><span class="sxs-lookup"><span data-stu-id="84609-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84609-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84609-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84609-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84609-108">Attributes and Elements</span></span>  
 <span data-ttu-id="84609-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84609-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84609-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="84609-110">Attributes</span></span>  
 <span data-ttu-id="84609-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="84609-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84609-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84609-112">Child Elements</span></span>  
  
|<span data-ttu-id="84609-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="84609-113">Element</span></span>|<span data-ttu-id="84609-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="84609-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84609-115">\<add></span><span class="sxs-lookup"><span data-stu-id="84609-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="84609-116">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="84609-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84609-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84609-117">Parent Elements</span></span>  
  
|<span data-ttu-id="84609-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="84609-118">Element</span></span>|<span data-ttu-id="84609-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="84609-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="84609-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84609-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="84609-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="84609-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84609-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="84609-122">Remarks</span></span>  
 <span data-ttu-id="84609-123">Você pode alterar o nível de uma opção de rastreamento colocando-a em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="84609-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="84609-124">Se o comutador for <xref:System.Diagnostics.BooleanSwitch>um, você poderá ativá-lo e desligá-lo.</span><span class="sxs-lookup"><span data-stu-id="84609-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="84609-125">Se o comutador for <xref:System.Diagnostics.TraceSwitch>um, você poderá atribuir diferentes níveis a ele para especificar os tipos de mensagens de rastreamento ou de depuração que o aplicativo gera.</span><span class="sxs-lookup"><span data-stu-id="84609-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84609-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84609-126">Example</span></span>  
 <span data-ttu-id="84609-127">O exemplo a seguir mostra como usar o elemento de  **\<> de opção** para `General` definir a opção de <xref:System.Diagnostics.TraceLevel> rastreamento para o nível e `Data` habilitar a opção de rastreamento booliano.</span><span class="sxs-lookup"><span data-stu-id="84609-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84609-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84609-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="84609-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="84609-129">Trace and Debug Settings Schema</span></span>](index.md)
