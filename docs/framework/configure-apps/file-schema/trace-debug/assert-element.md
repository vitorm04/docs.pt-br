---
title: Elemento <assert>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088942"
---
# <a name="assert-element"></a><span data-ttu-id="597b3-102">Elemento \<Assert ></span><span class="sxs-lookup"><span data-stu-id="597b3-102">\<assert> Element</span></span>
<span data-ttu-id="597b3-103">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="597b3-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

<span data-ttu-id="597b3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="597b3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="597b3-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="597b3-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="597b3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<assert >**</span><span class="sxs-lookup"><span data-stu-id="597b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**</span></span>

## <a name="syntax"></a><span data-ttu-id="597b3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="597b3-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="597b3-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="597b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="597b3-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="597b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="597b3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="597b3-110">Attributes</span></span>  
  
|<span data-ttu-id="597b3-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="597b3-111">Attribute</span></span>|<span data-ttu-id="597b3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="597b3-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="597b3-113">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="597b3-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="597b3-114">Especifica se uma caixa de mensagem deve ser exibida quando o método **debug. Assert** for avaliado como **false**.</span><span class="sxs-lookup"><span data-stu-id="597b3-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="597b3-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="597b3-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="597b3-116">Especifica o nome do arquivo no qual gravar a mensagem se **debug. Assert** for avaliado como **false**.</span><span class="sxs-lookup"><span data-stu-id="597b3-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="597b3-117">Atributo AssertUiEnabled</span><span class="sxs-lookup"><span data-stu-id="597b3-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="597b3-118">Valor</span><span class="sxs-lookup"><span data-stu-id="597b3-118">Value</span></span>|<span data-ttu-id="597b3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="597b3-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="597b3-120">Exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="597b3-120">Displays the message box.</span></span> <span data-ttu-id="597b3-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="597b3-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="597b3-122">Não exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="597b3-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="597b3-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="597b3-123">Child Elements</span></span>  
 <span data-ttu-id="597b3-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="597b3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="597b3-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="597b3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="597b3-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="597b3-126">Element</span></span>|<span data-ttu-id="597b3-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="597b3-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="597b3-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="597b3-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="597b3-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="597b3-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="597b3-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="597b3-130">Remarks</span></span>  
 <span data-ttu-id="597b3-131">Ambos os atributos no elemento **\<assert >** são opcionais.</span><span class="sxs-lookup"><span data-stu-id="597b3-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="597b3-132">Você pode desabilitar caixas de mensagens sem especificar um arquivo no qual gravar as mensagens ou pode especificar um arquivo para gravar mensagens enquanto deixa as caixas de mensagens habilitadas.</span><span class="sxs-lookup"><span data-stu-id="597b3-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="597b3-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="597b3-133">Example</span></span>  
 <span data-ttu-id="597b3-134">O exemplo a seguir mostra como desabilitar a exibição de caixas de mensagem quando você chama **debug. Assert** e grava as mensagens para `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="597b3-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="597b3-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="597b3-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="597b3-136">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="597b3-136">Trace and Debug Settings Schema</span></span>](index.md)
