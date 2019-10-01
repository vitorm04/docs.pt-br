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
ms.openlocfilehash: c161f842192396101dcc6850f3b3da328958eac3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697094"
---
# <a name="switches-element"></a><span data-ttu-id="44c53-102">\<switches > elemento</span><span class="sxs-lookup"><span data-stu-id="44c53-102">\<switches> Element</span></span>
<span data-ttu-id="44c53-103">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="44c53-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
[<span data-ttu-id="44c53-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="44c53-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="44c53-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="44c53-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="44c53-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<switches >**</span><span class="sxs-lookup"><span data-stu-id="44c53-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c53-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44c53-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44c53-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44c53-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44c53-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44c53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44c53-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="44c53-110">Attributes</span></span>  
 <span data-ttu-id="44c53-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="44c53-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44c53-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44c53-112">Child Elements</span></span>  
  
|<span data-ttu-id="44c53-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="44c53-113">Element</span></span>|<span data-ttu-id="44c53-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="44c53-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44c53-115">\<add></span><span class="sxs-lookup"><span data-stu-id="44c53-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="44c53-116">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="44c53-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44c53-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44c53-117">Parent Elements</span></span>  
  
|<span data-ttu-id="44c53-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="44c53-118">Element</span></span>|<span data-ttu-id="44c53-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="44c53-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44c53-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44c53-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="44c53-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="44c53-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c53-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="44c53-122">Remarks</span></span>  
 <span data-ttu-id="44c53-123">Você pode alterar o nível de uma opção de rastreamento colocando-a em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="44c53-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="44c53-124">Se a opção for um <xref:System.Diagnostics.BooleanSwitch>, você poderá ativá-la e desligá-la.</span><span class="sxs-lookup"><span data-stu-id="44c53-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="44c53-125">Se o comutador for um <xref:System.Diagnostics.TraceSwitch>, você poderá atribuir diferentes níveis a ele para especificar os tipos de mensagens de rastreamento ou de depuração que o aplicativo gera.</span><span class="sxs-lookup"><span data-stu-id="44c53-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44c53-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44c53-126">Example</span></span>  
 <span data-ttu-id="44c53-127">O exemplo a seguir mostra como usar o elemento **\<switch >** para definir a opção de rastreamento `General` para o nível <xref:System.Diagnostics.TraceLevel> e habilitar a opção de rastreamento booliano `Data`.</span><span class="sxs-lookup"><span data-stu-id="44c53-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44c53-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44c53-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="44c53-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="44c53-129">Trace and Debug Settings Schema</span></span>](index.md)
 