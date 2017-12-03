---
title: "Como fazer referência de forma consistente aos certificados X.509"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e92b3b4950e0a2edecc9a1f954a9f2959595c4e3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="f08d9-102">Como fazer referência de forma consistente aos certificados X.509</span><span class="sxs-lookup"><span data-stu-id="f08d9-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="f08d9-103">Você pode identificar um certificado de várias maneiras: pelo hash do certificado, o emissor e número de série ou pelo identificador de chave de assunto (SKI).</span><span class="sxs-lookup"><span data-stu-id="f08d9-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="f08d9-104">O SKI fornece uma identificação exclusiva para a chave pública da entidade do certificado e geralmente é usada ao trabalhar com a assinatura digital XML.</span><span class="sxs-lookup"><span data-stu-id="f08d9-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="f08d9-105">O valor SKI geralmente é parte do certificado x. 509 como um *a extensão de certificado x. 509*.</span><span class="sxs-lookup"><span data-stu-id="f08d9-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f08d9-106">tem um padrão *referenciando estilo* que usa o emissor e número de série, se a extensão SKI está ausente no certificado.</span><span class="sxs-lookup"><span data-stu-id="f08d9-106"> has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="f08d9-107">Se o certificado contém a extensão SKI, o padrão de referência de estilo usa o SKI para apontar para o certificado.</span><span class="sxs-lookup"><span data-stu-id="f08d9-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="f08d9-108">Se forma intermediário durante o desenvolvimento de um aplicativo, você alterna do uso de certificados que não usam a extensão SKI para certificados que usam a extensão SKI, o estilo de referência usada no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-geradas mensagens também as alterações.</span><span class="sxs-lookup"><span data-stu-id="f08d9-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-generated messages also changes.</span></span>  
  
 <span data-ttu-id="f08d9-109">Se um estilo consistente de referência for exigido, independentemente da presença da extensão SKI, é possível configurar o estilo de referência desejado, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f08d9-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f08d9-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f08d9-110">Example</span></span>  
 <span data-ttu-id="f08d9-111">O exemplo a seguir cria um elemento de associação de segurança personalizada que usa um único estilo de referência consistente, o nome do emissor e número de série.</span><span class="sxs-lookup"><span data-stu-id="f08d9-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f08d9-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f08d9-112">Compiling the Code</span></span>  
 <span data-ttu-id="f08d9-113">Os namespaces a seguir são necessários para compilar o código:</span><span class="sxs-lookup"><span data-stu-id="f08d9-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="f08d9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f08d9-114">See Also</span></span>  
 [<span data-ttu-id="f08d9-115">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="f08d9-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
