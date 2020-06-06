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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153224"
---
# <a name="switches-element"></a><span data-ttu-id="a867e-102">Elemento \<switches></span><span class="sxs-lookup"><span data-stu-id="a867e-102">\<switches> Element</span></span>
<span data-ttu-id="a867e-103">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="a867e-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="a867e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a867e-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a867e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a867e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a867e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a867e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a867e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a867e-107">Attributes</span></span>  
 <span data-ttu-id="a867e-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a867e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a867e-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a867e-109">Child Elements</span></span>  
  
|<span data-ttu-id="a867e-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="a867e-110">Element</span></span>|<span data-ttu-id="a867e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a867e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="a867e-112">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="a867e-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a867e-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a867e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a867e-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a867e-114">Element</span></span>|<span data-ttu-id="a867e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a867e-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a867e-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a867e-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="a867e-117">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="a867e-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a867e-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a867e-118">Remarks</span></span>  
 <span data-ttu-id="a867e-119">Você pode alterar o nível de uma opção de rastreamento colocando-a em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a867e-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="a867e-120">Se o comutador for um <xref:System.Diagnostics.BooleanSwitch> , você poderá ativá-lo e desligá-lo.</span><span class="sxs-lookup"><span data-stu-id="a867e-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="a867e-121">Se o comutador for um <xref:System.Diagnostics.TraceSwitch> , você poderá atribuir diferentes níveis a ele para especificar os tipos de mensagens de rastreamento ou de depuração que o aplicativo gera.</span><span class="sxs-lookup"><span data-stu-id="a867e-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a867e-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a867e-122">Example</span></span>  
 <span data-ttu-id="a867e-123">O exemplo a seguir mostra como usar o **\<switch>** elemento para definir a `General` opção de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar a `Data` opção de rastreamento booliano.</span><span class="sxs-lookup"><span data-stu-id="a867e-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a867e-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="a867e-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="a867e-125">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="a867e-125">Trace and Debug Settings Schema</span></span>](index.md)
