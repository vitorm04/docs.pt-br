---
title: Como criar certificados X.509 que podem ser acessados pelo WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: cd13eae0a72ceaf5abfb93dfe84a53cfc3c8dec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493700"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="a91e4-102">Como criar certificados X.509 que podem ser acessados pelo WCF</span><span class="sxs-lookup"><span data-stu-id="a91e4-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="a91e4-103">Para tornar um certificado x. 509 acessíveis para o Windows Communication Foundation (WCF), o código do aplicativo deve especificar o nome do repositório de certificado e o local.</span><span class="sxs-lookup"><span data-stu-id="a91e4-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="a91e4-104">Em determinadas circunstâncias, a identidade do processo deve ter acesso ao arquivo que contém a chave privada associada ao certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="a91e4-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="a91e4-105">Para obter a chave privada associada a um certificado x. 509 em um repositório de certificados, o WCF deve ter permissão para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="a91e4-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="a91e4-106">Por padrão, somente o proprietário e a conta do sistema podem acessar a chave privada de um certificado.</span><span class="sxs-lookup"><span data-stu-id="a91e4-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="a91e4-107">Para disponibilizar os certificados x. 509 para o WCF</span><span class="sxs-lookup"><span data-stu-id="a91e4-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="a91e4-108">Conceda à conta sob a qual WCF está executando o acesso de leitura para o arquivo que contém a chave privada associada ao certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="a91e4-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="a91e4-109">Determine se o WCF requer acesso de leitura à chave privada do certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="a91e4-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="a91e4-110">A tabela a seguir fornece detalhes sobre se uma chave privada deve estar disponível ao usar um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="a91e4-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="a91e4-111">Uso de certificados x. 509</span><span class="sxs-lookup"><span data-stu-id="a91e4-111">X.509 certificate use</span></span>|<span data-ttu-id="a91e4-112">Chave privada</span><span class="sxs-lookup"><span data-stu-id="a91e4-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="a91e4-113">Assinar digitalmente uma mensagem SOAP de saída.</span><span class="sxs-lookup"><span data-stu-id="a91e4-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="a91e4-114">Sim</span><span class="sxs-lookup"><span data-stu-id="a91e4-114">Yes</span></span>|  
        |<span data-ttu-id="a91e4-115">Verificar a assinatura de uma mensagem SOAP de entrada.</span><span class="sxs-lookup"><span data-stu-id="a91e4-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="a91e4-116">Não</span><span class="sxs-lookup"><span data-stu-id="a91e4-116">No</span></span>|  
        |<span data-ttu-id="a91e4-117">Criptografar uma mensagem SOAP de saída.</span><span class="sxs-lookup"><span data-stu-id="a91e4-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="a91e4-118">Não</span><span class="sxs-lookup"><span data-stu-id="a91e4-118">No</span></span>|  
        |<span data-ttu-id="a91e4-119">Descriptografar uma mensagem SOAP de entrada.</span><span class="sxs-lookup"><span data-stu-id="a91e4-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="a91e4-120">Sim</span><span class="sxs-lookup"><span data-stu-id="a91e4-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="a91e4-121">Determine o repositório de certificados local e o nome no qual o certificado é armazenado.</span><span class="sxs-lookup"><span data-stu-id="a91e4-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="a91e4-122">O repositório de certificados no qual o certificado é armazenado é especificado no código do aplicativo ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="a91e4-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="a91e4-123">Por exemplo, o exemplo a seguir especifica que o certificado está localizado no `CurrentUser` repositório de certificados denominado `My`.</span><span class="sxs-lookup"><span data-stu-id="a91e4-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="a91e4-124">Determinar onde a chave privada do certificado está localizada no computador usando o [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) ferramenta.</span><span class="sxs-lookup"><span data-stu-id="a91e4-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="a91e4-125">O [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) ferramenta requer o nome do repositório de certificados, repositório de certificados local e algo que identifica exclusivamente o certificado.</span><span class="sxs-lookup"><span data-stu-id="a91e4-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="a91e4-126">A ferramenta aceita o nome da entidade do certificado ou sua impressão digital como um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="a91e4-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="a91e4-127">Para obter mais informações sobre como determinar a impressão digital de um certificado, consulte [como: recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a91e4-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="a91e4-128">O seguinte exemplo de código usa o [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool para determinar o local da chave privada de um certificado no `My` armazenar em `CurrentUser` com uma impressão digital de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="a91e4-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="a91e4-129">Determine a conta que o WCF está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="a91e4-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="a91e4-130">A tabela a seguir fornece detalhes sobre a conta sob a qual o WCF está em execução para um determinado cenário.</span><span class="sxs-lookup"><span data-stu-id="a91e4-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="a91e4-131">Cenário</span><span class="sxs-lookup"><span data-stu-id="a91e4-131">Scenario</span></span>|<span data-ttu-id="a91e4-132">Identidade de processo</span><span class="sxs-lookup"><span data-stu-id="a91e4-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="a91e4-133">Cliente (console ou aplicativos WinForms).</span><span class="sxs-lookup"><span data-stu-id="a91e4-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="a91e4-134">Usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="a91e4-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="a91e4-135">Serviço auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="a91e4-135">Service that is self-hosted.</span></span>|<span data-ttu-id="a91e4-136">Usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="a91e4-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="a91e4-137">Serviço hospedado no IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) ou IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="a91e4-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="a91e4-138">SERVIÇO DE REDE</span><span class="sxs-lookup"><span data-stu-id="a91e4-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="a91e4-139">Serviço que é hospedado no IIS 5. x ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="a91e4-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="a91e4-140">Controlado pelo `<processModel>` elemento no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="a91e4-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="a91e4-141">A conta padrão é ASPNET.</span><span class="sxs-lookup"><span data-stu-id="a91e4-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="a91e4-142">Conceder acesso de leitura para o arquivo que contém a chave privada para a conta que o WCF está em execução, usando uma ferramenta como cacls.exe.</span><span class="sxs-lookup"><span data-stu-id="a91e4-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as cacls.exe.</span></span>  
  
         <span data-ttu-id="a91e4-143">Edições de exemplo de código a seguir (/ E) a lista de controle de acesso (ACL) para o arquivo especificado conceder (/ G) a conta de serviço de rede de leitura (: R) acesso ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="a91e4-143">The following code example edits (/E) the access control list (ACL) for the specified file to grant (/G) the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="a91e4-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a91e4-144">See Also</span></span>  
 [<span data-ttu-id="a91e4-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="a91e4-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [<span data-ttu-id="a91e4-146">Como recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="a91e4-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [<span data-ttu-id="a91e4-147">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="a91e4-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
