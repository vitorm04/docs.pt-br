---
title: '&lt;mailSettings&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 954755c7576e0ca4dd7946926c77e1e7e18055e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713948"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="0fe33-102">&lt;mailSettings&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="0fe33-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0fe33-103">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="0fe33-103">Configures mail sending options.</span></span>  

<span data-ttu-id="0fe33-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0fe33-104">\<configuration></span></span>  
<span data-ttu-id="0fe33-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0fe33-105">\<system.net></span></span>  
<span data-ttu-id="0fe33-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="0fe33-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe33-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fe33-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fe33-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0fe33-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0fe33-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0fe33-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fe33-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0fe33-110">Attributes</span></span>  
 <span data-ttu-id="0fe33-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0fe33-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fe33-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0fe33-112">Child Elements</span></span>  
  
|<span data-ttu-id="0fe33-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0fe33-113">Attribute</span></span>|<span data-ttu-id="0fe33-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fe33-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="0fe33-115">\<SMTP > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="0fe33-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="0fe33-116">Configura as opções de Simple Mail Transport Protocol.</span><span class="sxs-lookup"><span data-stu-id="0fe33-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fe33-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0fe33-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0fe33-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="0fe33-118">**Element**</span></span>|<span data-ttu-id="0fe33-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0fe33-119">**Description**</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="0fe33-120">Elemento [\<system.Net> (configurações de rede)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0fe33-120">[\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span></span>|<span data-ttu-id="0fe33-121">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="0fe33-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0fe33-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fe33-122">Example</span></span>  
 <span data-ttu-id="0fe33-123">O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="0fe33-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fe33-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fe33-124">See also</span></span>
- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="0fe33-125">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="0fe33-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
