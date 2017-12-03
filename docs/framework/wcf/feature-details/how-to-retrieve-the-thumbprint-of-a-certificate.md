---
title: "Como recuperar a impressão digital de um certificado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f66a7003fe712ab482d5237762e2bafffc5a6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a><span data-ttu-id="1bdf3-102">Como recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="1bdf3-102">How to: Retrieve the Thumbprint of a Certificate</span></span>
<span data-ttu-id="1bdf3-103">Ao escrever um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo que usa um certificado x. 509 para autenticação, geralmente é necessário especificar declarações encontradas no certificado.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-103">When writing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses an X.509 certificate for authentication, it is often necessary to specify claims found in the certificate.</span></span> <span data-ttu-id="1bdf3-104">Por exemplo, você deve fornecer uma declaração de impressão digital ao usar o <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeração no <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-104">For example, you must supply a thumbprint claim when using the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeration in the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="1bdf3-105">Localizar o valor da declaração requer duas etapas.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-105">Finding the claim value requires two steps.</span></span> <span data-ttu-id="1bdf3-106">Primeiro, abra o snap-in do Console de gerenciamento Microsoft (MMC) para certificados.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-106">First, open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="1bdf3-107">(Consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Segundo, conforme descrito aqui, localizar um certificado apropriado e copiar sua impressão digital (ou outros valores de declaração).</span><span class="sxs-lookup"><span data-stu-id="1bdf3-107">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Second, as described here, find an appropriate certificate and copy its thumbprint (or other claim values).</span></span>  
  
 <span data-ttu-id="1bdf3-108">Se você estiver usando um certificado para autenticação de serviço, é importante observar o valor de **emitido para** coluna (a primeira coluna no console).</span><span class="sxs-lookup"><span data-stu-id="1bdf3-108">If you are using a certificate for service authentication, it is important to note the value of the **Issued To** column (the first column in the console).</span></span> <span data-ttu-id="1bdf3-109">Ao usar o protocolo (SSL) como um segurança de transporte, uma das verificações primeiro feitas é comparar a base de dados de endereços identificador URI (Uniform Resource) de um serviço para o **emitido para** valor.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-109">When using Secure Sockets Layer (SSL) as a transport security, one of the first checks done is to compare the base address Uniform Resource Identifier (URI) of a service to the **Issued To** value.</span></span> <span data-ttu-id="1bdf3-110">Os valores devem coincidir ou o processo de autenticação é interrompido.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-110">The values must match or the authentication process is halted.</span></span>  
  
 <span data-ttu-id="1bdf3-111">Você também pode usar a ferramenta Makecert.exe do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK para criar certificados temporários para uso somente durante o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-111">You can also use the Makecert.exe tool from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK to create temporary certificates for use only during development.</span></span> <span data-ttu-id="1bdf3-112">Por padrão, no entanto, esse certificado não foi emitido por uma autoridade de certificação e não pode ser usado para fins de produção.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-112">By default, however, such a certificate is not issued by a certification authority, and is unusable for production purposes.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="1bdf3-113">[Como: criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).</span><span class="sxs-lookup"><span data-stu-id="1bdf3-113"> [How to: Create Temporary Certificates for Use During Development](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).</span></span>  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a><span data-ttu-id="1bdf3-114">Para recuperar a impressão digital do certificado</span><span class="sxs-lookup"><span data-stu-id="1bdf3-114">To retrieve a certificate's thumbprint</span></span>  
  
1.  <span data-ttu-id="1bdf3-115">Abra o snap-in do Console de gerenciamento Microsoft (MMC) para certificados.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-115">Open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="1bdf3-116">(Consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)</span><span class="sxs-lookup"><span data-stu-id="1bdf3-116">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)</span></span>  
  
2.  <span data-ttu-id="1bdf3-117">No **raiz do Console** janela esquerda do painel, clique em **certificados (computador Local)**.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-117">In the **Console Root** window's left pane, click **Certificates (Local Computer)**.</span></span>  
  
3.  <span data-ttu-id="1bdf3-118">Clique o **pessoal** para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-118">Click the **Personal** folder to expand it.</span></span>  
  
4.  <span data-ttu-id="1bdf3-119">Clique o **certificados** para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-119">Click the **Certificates** folder to expand it.</span></span>  
  
5.  <span data-ttu-id="1bdf3-120">Na lista de certificados, observe o **finalidades** título.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-120">In the list of certificates, note the **Intended Purposes** heading.</span></span> <span data-ttu-id="1bdf3-121">Localizar um certificado que lista **autenticação de cliente** como uma finalidade.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-121">Find a certificate that lists **Client Authentication** as an intended purpose.</span></span>  
  
6.  <span data-ttu-id="1bdf3-122">Clique duas vezes no certificado.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-122">Double-click the certificate.</span></span>  
  
7.  <span data-ttu-id="1bdf3-123">No **certificado** caixa de diálogo, clique o **detalhes** guia.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-123">In the **Certificate** dialog box, click the **Details** tab.</span></span>  
  
8.  <span data-ttu-id="1bdf3-124">Percorra a lista de campos e clique em **impressão digital**.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-124">Scroll through the list of fields and click **Thumbprint**.</span></span>  
  
9. <span data-ttu-id="1bdf3-125">Copie os caracteres hexadecimais da caixa.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-125">Copy the hexadecimal characters from the box.</span></span> <span data-ttu-id="1bdf3-126">Se essa impressão digital é usada no código para o `X509FindType`, remova os espaços entre os números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-126">If this thumbprint is used in code for the `X509FindType`, remove the spaces between the hexadecimal numbers.</span></span> <span data-ttu-id="1bdf3-127">Por exemplo, a impressão digital "a9 09 50 2d d8 2a e4 14 33 f8 de e6 38 86 7b de 2a de a3 77 do b0 0d 42" deve ser especificado como "a909502dd82ae41433e6f83886b00d4277a32a7b" no código.</span><span class="sxs-lookup"><span data-stu-id="1bdf3-127">For example, the thumbprint "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" should be specified as "a909502dd82ae41433e6f83886b00d4277a32a7b" in code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdf3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bdf3-128">See Also</span></span>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [<span data-ttu-id="1bdf3-129">Como: configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="1bdf3-129">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="1bdf3-130">Como: exibir certificados com o Snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="1bdf3-130">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="1bdf3-131">Como: criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="1bdf3-131">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
