---
title: Como exibir certificados com o snap-in do MMC
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5981e68ebe2870870fff5e92e87d7582ac2c42b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="76ae6-102">Como exibir certificados com o snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="76ae6-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="76ae6-103">Um tipo comum de credenciais é o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="76ae6-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="76ae6-104">Ao criar serviços ou clientes seguros, você poderá especificar que um certificado seja usado como a credencial de cliente ou serviço usando métodos como <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>.</span><span class="sxs-lookup"><span data-stu-id="76ae6-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="76ae6-105">O método exige vários parâmetros, como o armazenamento onde o certificado está armazenado e um valor para usar ao procurar pelo certificado.</span><span class="sxs-lookup"><span data-stu-id="76ae6-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="76ae6-106">O procedimento a seguir demonstra como examinar os repositórios em um computador para localizar um certificado apropriado.</span><span class="sxs-lookup"><span data-stu-id="76ae6-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="76ae6-107">Para obter um exemplo de encontrar a impressão digital do certificado, consulte [como: recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="76ae6-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="76ae6-108">Para exibir certificados no snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="76ae6-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="76ae6-109">Abra uma janela do Prompt de Comando.</span><span class="sxs-lookup"><span data-stu-id="76ae6-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="76ae6-110">Tipo `mmc` e pressione a tecla ENTER.</span><span class="sxs-lookup"><span data-stu-id="76ae6-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="76ae6-111">Observe que, para exibir certificados no armazenamento do computador local, você deverá estar na função de Administrador.</span><span class="sxs-lookup"><span data-stu-id="76ae6-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="76ae6-112">Sobre o **arquivo** menu, clique em **Adicionar/Remover Snap-In do**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="76ae6-113">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="76ae6-114">No **Adicionar Snap-in Standalone** caixa de diálogo, selecione **certificados**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="76ae6-115">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="76ae6-116">No **snap-in de certificados** caixa de diálogo, selecione **conta de computador** e clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="76ae6-117">Opcionalmente, você pode selecionar **conta de usuário Meus** ou **conta de serviço**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="76ae6-118">Se você não for administrador do computador, pode gerenciar certificados somente para sua conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="76ae6-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="76ae6-119">No **Selecionar computador** caixa de diálogo, clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="76ae6-120">No **Adicionar Snap-in Standalone** caixa de diálogo, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="76ae6-121">Sobre o **Adicionar/Remover Snap-in** caixa de diálogo, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="76ae6-122">No **raiz do Console** janela, clique em **certificados (computador Local)** para exibir o certificado armazena para o computador.</span><span class="sxs-lookup"><span data-stu-id="76ae6-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="76ae6-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="76ae6-123">Optional.</span></span> <span data-ttu-id="76ae6-124">Para exibir certificados para sua conta, repita as etapas de 3 a 6.</span><span class="sxs-lookup"><span data-stu-id="76ae6-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="76ae6-125">Na etapa 7, em vez de selecionar **conta de computador**, clique em **conta de usuário Meus** e repita as etapas 8 a 10.</span><span class="sxs-lookup"><span data-stu-id="76ae6-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="76ae6-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="76ae6-126">Optional.</span></span> <span data-ttu-id="76ae6-127">Sobre o **arquivo** menu, clique em **salvar** ou **Salvar como**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="76ae6-128">Salve o arquivo de console para reutilização posterior.</span><span class="sxs-lookup"><span data-stu-id="76ae6-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="76ae6-129">Exibindo certificados com o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="76ae6-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="76ae6-130">Você também pode exibir, exportar, importar e excluir certificados usando o Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="76ae6-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="76ae6-131">Para exibir certificados com o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="76ae6-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="76ae6-132">No Internet Explorer, clique em **ferramentas**, em seguida, clique em **opções da Internet** para exibir o **opções da Internet** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="76ae6-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="76ae6-133">Clique o **conteúdo** guia.</span><span class="sxs-lookup"><span data-stu-id="76ae6-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="76ae6-134">Em **certificados**, clique em **certificados**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="76ae6-135">Para exibir detalhes de qualquer certificado, selecione o certificado e clique em **exibição**.</span><span class="sxs-lookup"><span data-stu-id="76ae6-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ae6-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76ae6-136">See Also</span></span>  
 [<span data-ttu-id="76ae6-137">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="76ae6-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="76ae6-138">Como: criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="76ae6-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="76ae6-139">Como: recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="76ae6-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
