---
title: "&lt;specifiedPickupDirectory&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ffe34e6a811dd644b149a0fda12f1d1cd338c761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="0706f-102">&lt;specifiedPickupDirectory&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="0706f-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0706f-103">Configura o diretório local para um servidor de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="0706f-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="0706f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0706f-104">\<configuration></span></span>  
<span data-ttu-id="0706f-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="0706f-105">\<system.net></span></span>  
<span data-ttu-id="0706f-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="0706f-106">\<mailSettings></span></span>  
<span data-ttu-id="0706f-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="0706f-107">\<smtp></span></span>  
<span data-ttu-id="0706f-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="0706f-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0706f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0706f-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0706f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0706f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0706f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0706f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0706f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="0706f-112">Attributes</span></span>  
  
|<span data-ttu-id="0706f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0706f-113">Attribute</span></span>|<span data-ttu-id="0706f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0706f-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="0706f-115">O diretório onde salvar os aplicativos de email para processamento posterior pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="0706f-115">The directory where applications save e-mail for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0706f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0706f-116">Child Elements</span></span>  
 <span data-ttu-id="0706f-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0706f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0706f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0706f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0706f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="0706f-119">Element</span></span>|<span data-ttu-id="0706f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0706f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0706f-121">\<SMTP > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="0706f-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="0706f-122">Configura as opções de envio de mensagens de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="0706f-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0706f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="0706f-123">Remarks</span></span>  
 <span data-ttu-id="0706f-124">O `specifiedPickupDirectory` atributo define o diretório de onde aplicativos salvar mensagens de email a ser processada pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="0706f-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0706f-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0706f-125">Example</span></span>  
 <span data-ttu-id="0706f-126">O exemplo a seguir especifica c:\maildrop como o diretório de recebimento de email.</span><span class="sxs-lookup"><span data-stu-id="0706f-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0706f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0706f-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="0706f-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="0706f-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
