---
title: '&lt;specifiedPickupDirectory&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b62dc1a9118f7d4f1f693ade36626deaecd23999
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459731"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="2a006-102">&lt;specifiedPickupDirectory&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2a006-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2a006-103">Configura o diretório local para um servidor de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="2a006-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="2a006-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2a006-104">\<configuration></span></span>  
<span data-ttu-id="2a006-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2a006-105">\<system.net></span></span>  
<span data-ttu-id="2a006-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="2a006-106">\<mailSettings></span></span>  
<span data-ttu-id="2a006-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="2a006-107">\<smtp></span></span>  
<span data-ttu-id="2a006-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="2a006-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a006-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a006-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a006-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a006-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a006-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a006-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a006-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a006-112">Attributes</span></span>  
  
|<span data-ttu-id="2a006-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a006-113">Attribute</span></span>|<span data-ttu-id="2a006-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a006-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="2a006-115">O diretório em que os aplicativos salvam email para processamento posterior pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="2a006-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a006-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a006-116">Child Elements</span></span>  
 <span data-ttu-id="2a006-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2a006-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a006-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a006-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2a006-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a006-119">Element</span></span>|<span data-ttu-id="2a006-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a006-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a006-121">\<SMTP > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2a006-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="2a006-122">Configura as opções de envio de mensagens de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="2a006-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a006-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a006-123">Remarks</span></span>  
 <span data-ttu-id="2a006-124">O `specifiedPickupDirectory` atributo define o diretório em que os aplicativos salvam as mensagens de email a ser processada pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="2a006-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a006-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a006-125">Example</span></span>  
 <span data-ttu-id="2a006-126">O exemplo a seguir especifica c:\maildrop como o diretório de recebimento de email.</span><span class="sxs-lookup"><span data-stu-id="2a006-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a006-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a006-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="2a006-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2a006-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
