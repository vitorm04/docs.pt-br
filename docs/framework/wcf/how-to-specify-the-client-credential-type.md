---
title: 'Como: especificar o tipo de credencial de cliente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 1138f0fe955782c71076d5c15c236d1d4ebbec01
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185049"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="82a4b-102">Como: especificar o tipo de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="82a4b-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="82a4b-103">Depois de definir um modo de segurança (transporte ou mensagem), você tem a opção de configuração de tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="82a4b-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="82a4b-104">Esta propriedade especifica o tipo de credencial que o cliente deve fornecer para o serviço para autenticação.</span><span class="sxs-lookup"><span data-stu-id="82a4b-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="82a4b-105">Para obter mais informações sobre como definir o modo de segurança (uma etapa necessária antes de definir tipo de credencial de cliente), consulte [como: Definir o modo de segurança](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="82a4b-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="82a4b-106">Definir tipo de credencial de cliente no código</span><span class="sxs-lookup"><span data-stu-id="82a4b-106">To set the client credential type in code</span></span>  
  
1.  <span data-ttu-id="82a4b-107">Crie uma instância de associação que serão usadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="82a4b-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="82a4b-108">Este exemplo usa o <xref:System.ServiceModel.WSHttpBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="82a4b-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2.  <span data-ttu-id="82a4b-109">Defina a propriedade <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="82a4b-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="82a4b-110">Este exemplo usa o modo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="82a4b-110">This example uses the Message mode.</span></span>  
  
3.  <span data-ttu-id="82a4b-111">Defina a propriedade <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="82a4b-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="82a4b-112">Este exemplo define-o para usar a autenticação do Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="82a4b-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="82a4b-113">Para definir o tipo de credencial de cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="82a4b-113">To set the client credential type in configuration</span></span>  
  
1.  <span data-ttu-id="82a4b-114">Adicionar um [ \<System. ServiceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="82a4b-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="82a4b-115">Como um elemento filho, adicione uma [ \<associações >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="82a4b-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3.  <span data-ttu-id="82a4b-116">Adicione uma associação apropriada.</span><span class="sxs-lookup"><span data-stu-id="82a4b-116">Add an appropriate binding.</span></span> <span data-ttu-id="82a4b-117">Este exemplo usa o [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="82a4b-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4.  <span data-ttu-id="82a4b-118">Adicionar um [ \<associação >](../../../docs/framework/misc/binding.md) elemento e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="82a4b-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="82a4b-119">Este exemplo usa o nome "SecureBinding".</span><span class="sxs-lookup"><span data-stu-id="82a4b-119">This example uses the name "SecureBinding".</span></span>  
  
5.  <span data-ttu-id="82a4b-120">Adicionar um `<security>` associação.</span><span class="sxs-lookup"><span data-stu-id="82a4b-120">Add a `<security>` binding.</span></span> <span data-ttu-id="82a4b-121">Defina o `mode` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="82a4b-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="82a4b-122">Este exemplo define como `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="82a4b-122">This example sets it to `"Message"`.</span></span>  
  
6.  <span data-ttu-id="82a4b-123">Adicione uma `<message>` ou `<transport>` elemento, conforme determinado pelo modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="82a4b-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="82a4b-124">Defina o `clientCredentialType` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="82a4b-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="82a4b-125">Este exemplo usa `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="82a4b-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="82a4b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82a4b-126">See also</span></span>

- [<span data-ttu-id="82a4b-127">Serviços de segurança</span><span class="sxs-lookup"><span data-stu-id="82a4b-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="82a4b-128">Como: definir o modo de segurança</span><span class="sxs-lookup"><span data-stu-id="82a4b-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
