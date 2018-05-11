---
title: '&lt;Assert&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ab1644d23e4d6d78b62e701902e5ec39e134b38b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltassertgt-element"></a><span data-ttu-id="9f454-102">&lt;Assert&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="9f454-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="9f454-103">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="9f454-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="9f454-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9f454-104">\<configuration></span></span>  
<span data-ttu-id="9f454-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="9f454-105">\<system.diagnostics></span></span>  
<span data-ttu-id="9f454-106">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="9f454-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f454-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f454-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f454-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f454-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9f454-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f454-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f454-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f454-110">Attributes</span></span>  
  
|<span data-ttu-id="9f454-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f454-111">Attribute</span></span>|<span data-ttu-id="9f454-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f454-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="9f454-113">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9f454-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9f454-114">Especifica se exibir uma caixa de mensagem quando o **Assert** método é avaliada como **false**.</span><span class="sxs-lookup"><span data-stu-id="9f454-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="9f454-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9f454-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9f454-116">Especifica o nome do arquivo para gravar a mensagem se **Assert** é avaliada como **false**.</span><span class="sxs-lookup"><span data-stu-id="9f454-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="9f454-117">assertuienabled atributo</span><span class="sxs-lookup"><span data-stu-id="9f454-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="9f454-118">Valor</span><span class="sxs-lookup"><span data-stu-id="9f454-118">Value</span></span>|<span data-ttu-id="9f454-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f454-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="9f454-120">Exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9f454-120">Displays the message box.</span></span> <span data-ttu-id="9f454-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="9f454-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="9f454-122">Não exibir a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9f454-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f454-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f454-123">Child Elements</span></span>  
 <span data-ttu-id="9f454-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9f454-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f454-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f454-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9f454-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f454-126">Element</span></span>|<span data-ttu-id="9f454-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f454-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9f454-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f454-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9f454-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="9f454-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f454-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f454-130">Remarks</span></span>  
 <span data-ttu-id="9f454-131">Ambos os atributos no  **\<assert >** elemento são opcionais.</span><span class="sxs-lookup"><span data-stu-id="9f454-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="9f454-132">Você pode desabilitar as caixas de mensagem sem especificar um arquivo para gravar as mensagens para, ou você pode especificar um arquivo para gravar mensagens enquanto deixando habilitadas de caixas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9f454-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f454-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f454-133">Example</span></span>  
 <span data-ttu-id="9f454-134">O exemplo a seguir mostra como desabilitar Exibindo caixas de mensagem quando você chamar **Assert** e gravar as mensagens de `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="9f454-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f454-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f454-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="9f454-136">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="9f454-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
