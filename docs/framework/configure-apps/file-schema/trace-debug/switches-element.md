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
ms.openlocfilehash: 4aeb3cb0cd75f0fb27e3b359b86da61a77b491c7
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088798"
---
# <a name="switches-element"></a><span data-ttu-id="ab9fc-102">\<alternar > elemento</span><span class="sxs-lookup"><span data-stu-id="ab9fc-102">\<switches> Element</span></span>
<span data-ttu-id="ab9fc-103">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="ab9fc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab9fc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ab9fc-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab9fc-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="ab9fc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<opções >**</span><span class="sxs-lookup"><span data-stu-id="ab9fc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ab9fc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab9fc-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab9fc-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ab9fc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ab9fc-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab9fc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ab9fc-110">Attributes</span></span>  
 <span data-ttu-id="ab9fc-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab9fc-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ab9fc-112">Child Elements</span></span>  
  
|<span data-ttu-id="ab9fc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab9fc-113">Element</span></span>|<span data-ttu-id="ab9fc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab9fc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab9fc-115">\<add></span><span class="sxs-lookup"><span data-stu-id="ab9fc-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="ab9fc-116">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab9fc-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ab9fc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ab9fc-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab9fc-118">Element</span></span>|<span data-ttu-id="ab9fc-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab9fc-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ab9fc-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="ab9fc-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab9fc-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab9fc-122">Remarks</span></span>  
 <span data-ttu-id="ab9fc-123">Você pode alterar o nível de uma opção de rastreamento colocando-a em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="ab9fc-124">Se a opção for uma <xref:System.Diagnostics.BooleanSwitch>, você poderá ativá-la e desligá-la.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="ab9fc-125">Se o comutador for um <xref:System.Diagnostics.TraceSwitch>, você poderá atribuir diferentes níveis a ele para especificar os tipos de mensagens de rastreamento ou de depuração que o aplicativo gera.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab9fc-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab9fc-126">Example</span></span>  
 <span data-ttu-id="ab9fc-127">O exemplo a seguir mostra como usar o elemento **\<switch >** para definir a opção de rastreamento de `General` para o nível de <xref:System.Diagnostics.TraceLevel> e habilitar a opção de rastreamento booliano de `Data`.</span><span class="sxs-lookup"><span data-stu-id="ab9fc-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab9fc-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab9fc-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="ab9fc-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="ab9fc-129">Trace and Debug Settings Schema</span></span>](index.md)
