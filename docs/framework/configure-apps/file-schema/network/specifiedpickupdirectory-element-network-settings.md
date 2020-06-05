---
title: Elemento <specifiedPickupDirectory> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "79154602"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="bb1e3-102">Elemento \<specifiedPickupDirectory> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="bb1e3-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="bb1e3-103">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="bb1e3-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="bb1e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb1e3-104">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb1e3-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bb1e3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bb1e3-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bb1e3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb1e3-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="bb1e3-107">Attributes</span></span>  
  
|<span data-ttu-id="bb1e3-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="bb1e3-108">Attribute</span></span>|<span data-ttu-id="bb1e3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb1e3-109">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="bb1e3-110">O diretório em que os aplicativos salvam o email para processamento posterior pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="bb1e3-110">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb1e3-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bb1e3-111">Child Elements</span></span>  
 <span data-ttu-id="bb1e3-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bb1e3-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb1e3-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bb1e3-113">Parent Elements</span></span>  
  
|<span data-ttu-id="bb1e3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="bb1e3-114">Element</span></span>|<span data-ttu-id="bb1e3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb1e3-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb1e3-116">\<smtp>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="bb1e3-116">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="bb1e3-117">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="bb1e3-117">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb1e3-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb1e3-118">Remarks</span></span>  
 <span data-ttu-id="bb1e3-119">O `specifiedPickupDirectory` atributo define o diretório em que os aplicativos salvam mensagens de email a serem processadas pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="bb1e3-119">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb1e3-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb1e3-120">Example</span></span>  
 <span data-ttu-id="bb1e3-121">O exemplo a seguir especifica c:\maildrop como o diretório de recebimento de email.</span><span class="sxs-lookup"><span data-stu-id="bb1e3-121">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb1e3-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb1e3-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="bb1e3-123">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="bb1e3-123">Network Settings Schema</span></span>](index.md)
