---
title: Elemento <add> para <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088952"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="08d14-102">\<Adicionar > elemento para \<switches ></span><span class="sxs-lookup"><span data-stu-id="08d14-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="08d14-103">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="08d14-103">Specifies the level where a trace switch is set.</span></span>  

<span data-ttu-id="08d14-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="08d14-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="08d14-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="08d14-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="08d14-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<opções**](switches-element.md) ></span><span class="sxs-lookup"><span data-stu-id="08d14-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)</span></span>\
<span data-ttu-id="08d14-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**adicionar >**</span><span class="sxs-lookup"><span data-stu-id="08d14-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="08d14-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08d14-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08d14-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08d14-109">Attributes and Elements</span></span>  
 <span data-ttu-id="08d14-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08d14-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08d14-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="08d14-111">Attributes</span></span>  
  
|<span data-ttu-id="08d14-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="08d14-112">Attribute</span></span>|<span data-ttu-id="08d14-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="08d14-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08d14-114">**name**</span><span class="sxs-lookup"><span data-stu-id="08d14-114">**name**</span></span>|<span data-ttu-id="08d14-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="08d14-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="08d14-116">Especifica o nome da opção.</span><span class="sxs-lookup"><span data-stu-id="08d14-116">Specifies the name of the switch.</span></span> <span data-ttu-id="08d14-117">O valor desse atributo corresponde ao parâmetro *DisplayName* que é passado para o Construtor switch.</span><span class="sxs-lookup"><span data-stu-id="08d14-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="08d14-118">**value**</span><span class="sxs-lookup"><span data-stu-id="08d14-118">**value**</span></span>|<span data-ttu-id="08d14-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="08d14-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="08d14-120">Especifica o nível da opção.</span><span class="sxs-lookup"><span data-stu-id="08d14-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08d14-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08d14-121">Child Elements</span></span>  
 <span data-ttu-id="08d14-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="08d14-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08d14-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08d14-123">Parent Elements</span></span>  
  
|<span data-ttu-id="08d14-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="08d14-124">Element</span></span>|<span data-ttu-id="08d14-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="08d14-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="08d14-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08d14-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="08d14-127">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="08d14-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="08d14-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="08d14-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d14-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="08d14-129">Remarks</span></span>  
 <span data-ttu-id="08d14-130">Você pode alterar o nível de uma opção de rastreamento colocando-a em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="08d14-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="08d14-131">Se a opção for uma <xref:System.Diagnostics.BooleanSwitch>, você poderá ativá-la e desligá-la.</span><span class="sxs-lookup"><span data-stu-id="08d14-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="08d14-132">Se o comutador for um <xref:System.Diagnostics.TraceSwitch>, você poderá atribuir diferentes níveis a ele para especificar os tipos de mensagens de rastreamento ou de depuração que o aplicativo gera.</span><span class="sxs-lookup"><span data-stu-id="08d14-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08d14-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08d14-133">Example</span></span>  
 <span data-ttu-id="08d14-134">O exemplo a seguir mostra como usar o elemento **\<adicionar >** para definir a opção de rastreamento de `General` para o nível de <xref:System.Diagnostics.TraceLevel> e habilitar a opção de rastreamento booliano de `Data`.</span><span class="sxs-lookup"><span data-stu-id="08d14-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08d14-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08d14-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="08d14-136">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="08d14-136">Trace and Debug Settings Schema</span></span>](index.md)
