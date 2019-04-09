---
title: <mailSettings> (Configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 54fb68ab0bf8aa2665d70391350c626131ccb4bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180616"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="76651-102">\<mailSettings > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="76651-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="76651-103">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="76651-103">Configures mail sending options.</span></span>  

<span data-ttu-id="76651-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="76651-104">\<configuration></span></span>  
<span data-ttu-id="76651-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="76651-105">\<system.net></span></span>  
<span data-ttu-id="76651-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="76651-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76651-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76651-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76651-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="76651-108">Attributes and Elements</span></span>  
 <span data-ttu-id="76651-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="76651-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76651-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="76651-110">Attributes</span></span>  
 <span data-ttu-id="76651-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="76651-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76651-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="76651-112">Child Elements</span></span>  
  
|<span data-ttu-id="76651-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="76651-113">Attribute</span></span>|<span data-ttu-id="76651-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="76651-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="76651-115">\<SMTP > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="76651-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="76651-116">Configura as opções de Simple Mail Transport Protocol.</span><span class="sxs-lookup"><span data-stu-id="76651-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76651-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="76651-117">Parent Elements</span></span>  
  
|**<span data-ttu-id="76651-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="76651-118">Element</span></span>**|**<span data-ttu-id="76651-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="76651-119">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="76651-120">\<system.Net > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="76651-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="76651-121">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="76651-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76651-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76651-122">Example</span></span>  
 <span data-ttu-id="76651-123">O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="76651-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76651-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76651-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="76651-125">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="76651-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
