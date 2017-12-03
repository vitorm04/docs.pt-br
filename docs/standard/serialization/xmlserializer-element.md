---
title: Elemento &lt;xmlSerializer&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17e4fcd1b471a5197f2e6a30bad10cbdbe22f216
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="6c15a-102">Elemento &lt;xmlSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="6c15a-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="6c15a-103">Especifica se uma verificação adicional de progresso do <xref:System.Xml.Serialization.XmlSerializer> é feita.</span><span class="sxs-lookup"><span data-stu-id="6c15a-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="6c15a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6c15a-104">\<configuration></span></span>  
<span data-ttu-id="6c15a-105">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="6c15a-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c15a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c15a-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c15a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c15a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6c15a-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c15a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c15a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c15a-109">Attributes</span></span>  
  
|<span data-ttu-id="6c15a-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="6c15a-110">Attribute</span></span>|<span data-ttu-id="6c15a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c15a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c15a-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="6c15a-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="6c15a-113">Especifica se o progresso do <xref:System.Xml.Serialization.XmlSerializer> é verificado.</span><span class="sxs-lookup"><span data-stu-id="6c15a-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="6c15a-114">Defina o atributo como "true" ou "false".</span><span class="sxs-lookup"><span data-stu-id="6c15a-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="6c15a-115">O padrão é "true".</span><span class="sxs-lookup"><span data-stu-id="6c15a-115">The default is "true".</span></span>|  
|<span data-ttu-id="6c15a-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="6c15a-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="6c15a-117">Especifica se o <xref:System.Xml.Serialization.XmlSerializer> usa a geração de serialização herdada que gera assemblies escrevendo código C# em um arquivo e, em seguida, compilando-o em um assembly.</span><span class="sxs-lookup"><span data-stu-id="6c15a-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="6c15a-118">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="6c15a-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c15a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c15a-119">Child Elements</span></span>  
 <span data-ttu-id="6c15a-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6c15a-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c15a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c15a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6c15a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c15a-122">Element</span></span>|<span data-ttu-id="6c15a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c15a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c15a-124">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="6c15a-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="6c15a-125">Contém definições de configuração para as classes <xref:System.Xml.Serialization.XmlSerializer> e <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="6c15a-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c15a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c15a-126">Remarks</span></span>  
 <span data-ttu-id="6c15a-127">Por padrão, o <xref:System.Xml.Serialization.XmlSerializer> fornece uma camada adicional de segurança contra potenciais ataques de negação de serviço ao desserializar dados não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="6c15a-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="6c15a-128">Ele faz isso tentando detectar loops infinitos durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="6c15a-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="6c15a-129">Se uma condição desse tipo for detectada, uma exceção será gerada com a seguinte mensagem: “Erro interno: a desserialização não pôde avançar sobre o fluxo subjacente”.</span><span class="sxs-lookup"><span data-stu-id="6c15a-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="6c15a-130">Receber essa mensagem não necessariamente indica que um ataque de negação de serviço esteja em andamento.</span><span class="sxs-lookup"><span data-stu-id="6c15a-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="6c15a-131">Em algumas circunstâncias raras, o mecanismo de detecção de loop infinito produz um falso positivo e a exceção é gerada para uma mensagem de entrada legítima.</span><span class="sxs-lookup"><span data-stu-id="6c15a-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="6c15a-132">Se você achar que em seus aplicativos específicos mensagens legítimas estão sendo rejeitadas por essa camada extra de proteção, defina o atributo **checkDeserializeAdvances** como “false”.</span><span class="sxs-lookup"><span data-stu-id="6c15a-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c15a-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c15a-133">Example</span></span>  
 <span data-ttu-id="6c15a-134">O exemplo de código a seguir define o atributo **checkDeserializeAdvances** como “false”.</span><span class="sxs-lookup"><span data-stu-id="6c15a-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c15a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c15a-135">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="6c15a-136">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="6c15a-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="6c15a-137">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="6c15a-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
