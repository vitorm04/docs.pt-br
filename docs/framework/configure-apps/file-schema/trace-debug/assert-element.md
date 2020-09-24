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
ms.openlocfilehash: eb29701912a45a484b1716195b449e8a97d1d4b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149290"
---
# <a name="assert-element"></a><span data-ttu-id="9c00b-102">Elemento \<assert></span><span class="sxs-lookup"><span data-stu-id="9c00b-102">\<assert> Element</span></span>

<span data-ttu-id="9c00b-103">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="9c00b-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="9c00b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c00b-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c00b-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c00b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9c00b-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c00b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c00b-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c00b-107">Attributes</span></span>  
  
|<span data-ttu-id="9c00b-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c00b-108">Attribute</span></span>|<span data-ttu-id="9c00b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c00b-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="9c00b-110">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9c00b-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9c00b-111">Especifica se uma caixa de mensagem deve ser exibida quando o método **debug. Assert** for avaliado como **false**.</span><span class="sxs-lookup"><span data-stu-id="9c00b-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="9c00b-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9c00b-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9c00b-113">Especifica o nome do arquivo no qual gravar a mensagem se **debug. Assert** for avaliado como **false**.</span><span class="sxs-lookup"><span data-stu-id="9c00b-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="9c00b-114">Atributo AssertUiEnabled</span><span class="sxs-lookup"><span data-stu-id="9c00b-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="9c00b-115">Valor</span><span class="sxs-lookup"><span data-stu-id="9c00b-115">Value</span></span>|<span data-ttu-id="9c00b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c00b-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="9c00b-117">Exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9c00b-117">Displays the message box.</span></span> <span data-ttu-id="9c00b-118">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="9c00b-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="9c00b-119">Não exibe a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9c00b-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c00b-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c00b-120">Child Elements</span></span>  

 <span data-ttu-id="9c00b-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9c00b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c00b-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c00b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9c00b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c00b-123">Element</span></span>|<span data-ttu-id="9c00b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c00b-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9c00b-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c00b-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9c00b-126">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="9c00b-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c00b-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c00b-127">Remarks</span></span>  

 <span data-ttu-id="9c00b-128">Ambos os atributos no **\<assert>** elemento são opcionais.</span><span class="sxs-lookup"><span data-stu-id="9c00b-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="9c00b-129">Você pode desabilitar caixas de mensagens sem especificar um arquivo no qual gravar as mensagens ou pode especificar um arquivo para gravar mensagens enquanto deixa as caixas de mensagens habilitadas.</span><span class="sxs-lookup"><span data-stu-id="9c00b-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c00b-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c00b-130">Example</span></span>  

 <span data-ttu-id="9c00b-131">O exemplo a seguir mostra como desabilitar a exibição de caixas de mensagem quando você chama **debug. Assert** e grava as mensagens em `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="9c00b-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c00b-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c00b-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="9c00b-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="9c00b-133">Trace and Debug Settings Schema</span></span>](index.md)
