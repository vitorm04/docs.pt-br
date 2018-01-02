---
title: '&lt;Assert&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9670cf0faa3e7f69b8f99b09fa26741991a60481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltassertgt-element"></a><span data-ttu-id="edab8-102">&lt;Assert&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="edab8-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="edab8-103">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="edab8-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="edab8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="edab8-104">\<configuration></span></span>  
<span data-ttu-id="edab8-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="edab8-105">\<system.diagnostics></span></span>  
<span data-ttu-id="edab8-106">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="edab8-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edab8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edab8-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edab8-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="edab8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="edab8-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="edab8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edab8-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="edab8-110">Attributes</span></span>  
  
|<span data-ttu-id="edab8-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="edab8-111">Attribute</span></span>|<span data-ttu-id="edab8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="edab8-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="edab8-113">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="edab8-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="edab8-114">Especifica se exibir uma caixa de mensagem quando o **Assert** método é avaliada como **false**.</span><span class="sxs-lookup"><span data-stu-id="edab8-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="edab8-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="edab8-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="edab8-116">Especifica o nome do arquivo para gravar a mensagem se **Assert** é avaliada como **false**.</span><span class="sxs-lookup"><span data-stu-id="edab8-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="edab8-117">assertuienabled atributo</span><span class="sxs-lookup"><span data-stu-id="edab8-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="edab8-118">Valor</span><span class="sxs-lookup"><span data-stu-id="edab8-118">Value</span></span>|<span data-ttu-id="edab8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="edab8-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="edab8-120">Exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="edab8-120">Displays the message box.</span></span> <span data-ttu-id="edab8-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="edab8-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="edab8-122">Não exibir a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="edab8-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edab8-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="edab8-123">Child Elements</span></span>  
 <span data-ttu-id="edab8-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="edab8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="edab8-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="edab8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="edab8-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="edab8-126">Element</span></span>|<span data-ttu-id="edab8-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="edab8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="edab8-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="edab8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="edab8-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="edab8-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edab8-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="edab8-130">Remarks</span></span>  
 <span data-ttu-id="edab8-131">Ambos os atributos no  **\<assert >** elemento são opcionais.</span><span class="sxs-lookup"><span data-stu-id="edab8-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="edab8-132">Você pode desabilitar as caixas de mensagem sem especificar um arquivo para gravar as mensagens para, ou você pode especificar um arquivo para gravar mensagens enquanto deixando habilitadas de caixas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="edab8-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edab8-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="edab8-133">Example</span></span>  
 <span data-ttu-id="edab8-134">O exemplo a seguir mostra como desabilitar Exibindo caixas de mensagem quando você chamar **Assert** e gravar as mensagens de `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="edab8-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="edab8-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edab8-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="edab8-136">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="edab8-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
