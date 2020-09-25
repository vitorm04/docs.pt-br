---
title: <transport> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 81c52405478d4c1ab5c65aab73f7feff61b879d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178015"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="4dddb-102">\<transport> de \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="4dddb-102">\<transport> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="4dddb-103">Define as configurações de segurança de transporte para um pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="4dddb-103">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="4dddb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4dddb-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dddb-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4dddb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4dddb-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4dddb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dddb-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="4dddb-107">Attributes</span></span>  
  
|<span data-ttu-id="4dddb-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="4dddb-108">Attribute</span></span>|<span data-ttu-id="4dddb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dddb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dddb-110">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="4dddb-110">protectionLevel</span></span>|<span data-ttu-id="4dddb-111">Define o nível de proteção do pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="4dddb-111">Defines protection level of the named pipe.</span></span> <span data-ttu-id="4dddb-112">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="4dddb-112">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="4dddb-113">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="4dddb-113">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="4dddb-114">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="4dddb-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4dddb-115">-Nenhum: sem proteção.</span><span class="sxs-lookup"><span data-stu-id="4dddb-115">-   None: No protection.</span></span><br /><span data-ttu-id="4dddb-116">-Sign: as mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="4dddb-116">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="4dddb-117">-EncryptAndSign: as mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="4dddb-117">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="4dddb-118">O valor padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="4dddb-118">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dddb-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4dddb-119">Child Elements</span></span>  

 <span data-ttu-id="4dddb-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4dddb-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dddb-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4dddb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4dddb-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4dddb-122">Element</span></span>|<span data-ttu-id="4dddb-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dddb-123">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="4dddb-124">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="4dddb-124">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dddb-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="4dddb-125">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="4dddb-126">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4dddb-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4dddb-127">Associações</span><span class="sxs-lookup"><span data-stu-id="4dddb-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4dddb-128">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="4dddb-128">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4dddb-129">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4dddb-129">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
