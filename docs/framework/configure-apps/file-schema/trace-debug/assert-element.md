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
ms.openlocfilehash: 2f3823265e358976f970cdfa36772d2251894280
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701353"
---
# <a name="assert-element"></a><span data-ttu-id="fb3cc-102">\<Assert > elemento</span><span class="sxs-lookup"><span data-stu-id="fb3cc-102">\<assert> Element</span></span>
<span data-ttu-id="fb3cc-103">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="fb3cc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fb3cc-104">\<configuration></span></span>  
<span data-ttu-id="fb3cc-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="fb3cc-105">\<system.diagnostics></span></span>  
<span data-ttu-id="fb3cc-106">\<assert></span><span class="sxs-lookup"><span data-stu-id="fb3cc-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3cc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb3cc-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb3cc-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fb3cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fb3cc-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb3cc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb3cc-110">Attributes</span></span>  
  
|<span data-ttu-id="fb3cc-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="fb3cc-111">Attribute</span></span>|<span data-ttu-id="fb3cc-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3cc-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="fb3cc-113">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fb3cc-114">Especifica se exibir uma caixa de mensagem quando o **Debug. Assert** método é avaliada como **falso**.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="fb3cc-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fb3cc-116">Especifica o nome do arquivo para gravar a mensagem se **Debug. Assert** é avaliada como **falso**.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="fb3cc-117">assertuienabled atributo</span><span class="sxs-lookup"><span data-stu-id="fb3cc-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="fb3cc-118">Valor</span><span class="sxs-lookup"><span data-stu-id="fb3cc-118">Value</span></span>|<span data-ttu-id="fb3cc-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3cc-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="fb3cc-120">Exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-120">Displays the message box.</span></span> <span data-ttu-id="fb3cc-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="fb3cc-122">Não exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb3cc-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fb3cc-123">Child Elements</span></span>  
 <span data-ttu-id="fb3cc-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb3cc-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fb3cc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fb3cc-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb3cc-126">Element</span></span>|<span data-ttu-id="fb3cc-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3cc-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fb3cc-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fb3cc-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb3cc-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb3cc-130">Remarks</span></span>  
 <span data-ttu-id="fb3cc-131">Ambos os atributos na  **\<assert >** elemento são opcionais.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="fb3cc-132">Você pode desabilitar as caixas de mensagem sem especificar um arquivo para gravar as mensagens de, ou você pode especificar um arquivo para gravar mensagens enquanto deixando habilitadas de caixas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb3cc-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb3cc-133">Example</span></span>  
 <span data-ttu-id="fb3cc-134">O exemplo a seguir mostra como desabilitar Exibindo caixas de mensagem quando você chama **Debug. Assert** e gravar as mensagens para `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="fb3cc-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb3cc-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb3cc-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="fb3cc-136">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="fb3cc-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
