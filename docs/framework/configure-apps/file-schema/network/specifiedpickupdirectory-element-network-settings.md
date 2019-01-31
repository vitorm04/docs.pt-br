---
title: Elemento <specifiedPickupDirectory> (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 6abee1b01e690633dabfd225b30fcb9b8b408dad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270817"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="370d9-102">\<specifiedPickupDirectory > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="370d9-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="370d9-103">Configura o diretório local para um servidor de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="370d9-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="370d9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="370d9-104">\<configuration></span></span>  
<span data-ttu-id="370d9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="370d9-105">\<system.net></span></span>  
<span data-ttu-id="370d9-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="370d9-106">\<mailSettings></span></span>  
<span data-ttu-id="370d9-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="370d9-107">\<smtp></span></span>  
<span data-ttu-id="370d9-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="370d9-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="370d9-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="370d9-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="370d9-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="370d9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="370d9-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="370d9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="370d9-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="370d9-112">Attributes</span></span>  
  
|<span data-ttu-id="370d9-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="370d9-113">Attribute</span></span>|<span data-ttu-id="370d9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="370d9-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="370d9-115">O diretório em que os aplicativos salvam email para processamento posterior pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="370d9-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="370d9-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="370d9-116">Child Elements</span></span>  
 <span data-ttu-id="370d9-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="370d9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="370d9-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="370d9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="370d9-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="370d9-119">Element</span></span>|<span data-ttu-id="370d9-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="370d9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="370d9-121">\<SMTP > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="370d9-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="370d9-122">Configura as opções de envio de mensagens de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="370d9-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="370d9-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="370d9-123">Remarks</span></span>  
 <span data-ttu-id="370d9-124">O `specifiedPickupDirectory` atributo define o diretório em que os aplicativos salvam as mensagens de email a ser processada pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="370d9-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="370d9-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="370d9-125">Example</span></span>  
 <span data-ttu-id="370d9-126">O exemplo a seguir especifica c:\maildrop como o diretório de recebimento de email.</span><span class="sxs-lookup"><span data-stu-id="370d9-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="370d9-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="370d9-127">See also</span></span>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="370d9-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="370d9-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
