---
title: Elemento <add> para <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 5be39425363cb6d2a0eca6a0fa3f4154ce857bb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173933"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="01872-102">Elemento \<add> para \<switches></span><span class="sxs-lookup"><span data-stu-id="01872-102">\<add> Element for \<switches></span></span>

<span data-ttu-id="01872-103">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="01872-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="01872-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01872-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01872-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="01872-105">Attributes and Elements</span></span>  

 <span data-ttu-id="01872-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="01872-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01872-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="01872-107">Attributes</span></span>  
  
|<span data-ttu-id="01872-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="01872-108">Attribute</span></span>|<span data-ttu-id="01872-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="01872-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01872-110">**name**</span><span class="sxs-lookup"><span data-stu-id="01872-110">**name**</span></span>|<span data-ttu-id="01872-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="01872-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="01872-112">Especifica o nome da opção.</span><span class="sxs-lookup"><span data-stu-id="01872-112">Specifies the name of the switch.</span></span> <span data-ttu-id="01872-113">O valor desse atributo corresponde ao parâmetro *DisplayName* que é passado para o Construtor switch.</span><span class="sxs-lookup"><span data-stu-id="01872-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="01872-114">**value**</span><span class="sxs-lookup"><span data-stu-id="01872-114">**value**</span></span>|<span data-ttu-id="01872-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="01872-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="01872-116">Especifica o nível da opção.</span><span class="sxs-lookup"><span data-stu-id="01872-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01872-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="01872-117">Child Elements</span></span>  

 <span data-ttu-id="01872-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="01872-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01872-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="01872-119">Parent Elements</span></span>  
  
|<span data-ttu-id="01872-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="01872-120">Element</span></span>|<span data-ttu-id="01872-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="01872-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="01872-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="01872-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="01872-123">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="01872-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="01872-124">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="01872-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01872-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="01872-125">Remarks</span></span>  

 <span data-ttu-id="01872-126">Você pode alterar o nível de uma opção de rastreamento colocando-a em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="01872-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="01872-127">Se o comutador for um <xref:System.Diagnostics.BooleanSwitch> , você poderá ativá-lo e desligá-lo.</span><span class="sxs-lookup"><span data-stu-id="01872-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="01872-128">Se o comutador for um <xref:System.Diagnostics.TraceSwitch> , você poderá atribuir diferentes níveis a ele para especificar os tipos de mensagens de rastreamento ou de depuração que o aplicativo gera.</span><span class="sxs-lookup"><span data-stu-id="01872-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01872-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01872-129">Example</span></span>  

 <span data-ttu-id="01872-130">O exemplo a seguir mostra como usar o **\<add>** elemento para definir a `General` opção de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar a `Data` opção de rastreamento booliano.</span><span class="sxs-lookup"><span data-stu-id="01872-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01872-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="01872-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="01872-132">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="01872-132">Trace and Debug Settings Schema</span></span>](index.md)
