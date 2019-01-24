---
title: 'Como: Exibir certificados com o Snap-in do MMC'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 72fd6a1be2f33e1bfeb08fd43f3436627ee842e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521576"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="d3f75-102">Como: Exibir certificados com o Snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="d3f75-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="d3f75-103">Um tipo comum de credenciais é o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="d3f75-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="d3f75-104">Ao criar serviços ou clientes seguros, você poderá especificar que um certificado seja usado como a credencial de cliente ou serviço usando métodos como <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3f75-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="d3f75-105">O método exige vários parâmetros, como o armazenamento onde o certificado está armazenado e um valor para usar ao procurar pelo certificado.</span><span class="sxs-lookup"><span data-stu-id="d3f75-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="d3f75-106">O procedimento a seguir demonstra como examinar os repositórios em um computador para localizar um certificado apropriado.</span><span class="sxs-lookup"><span data-stu-id="d3f75-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="d3f75-107">Para obter um exemplo de encontrar a impressão digital do certificado, consulte [como: Recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="d3f75-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="d3f75-108">Para exibir certificados no snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="d3f75-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="d3f75-109">Abra uma janela do Prompt de Comando.</span><span class="sxs-lookup"><span data-stu-id="d3f75-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="d3f75-110">Tipo `mmc` e pressione a tecla ENTER.</span><span class="sxs-lookup"><span data-stu-id="d3f75-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="d3f75-111">Observe que, para exibir certificados no armazenamento do computador local, você deverá estar na função de Administrador.</span><span class="sxs-lookup"><span data-stu-id="d3f75-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="d3f75-112">Sobre o **arquivo** menu, clique em **Adicionar/Remover Snap-In do**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="d3f75-113">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="d3f75-114">No **Adicionar Snap-in Standalone** caixa de diálogo, selecione **certificados**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="d3f75-115">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="d3f75-116">No **snap-in de certificados** caixa de diálogo, selecione **conta de computador** e clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="d3f75-117">Opcionalmente, você pode selecionar **minha conta de usuário** ou **conta de serviço**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="d3f75-118">Se você não for administrador do computador, pode gerenciar certificados somente para sua conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="d3f75-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="d3f75-119">No **Selecionar computador** caixa de diálogo, clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="d3f75-120">No **Adicionar Snap-in Standalone** caixa de diálogo, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="d3f75-121">Sobre o **Adicionar/Remover Snap-in** caixa de diálogo, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="d3f75-122">No **raiz do Console** janela, clique em **certificados (computador Local)** para exibir o certificado armazenamentos para o computador.</span><span class="sxs-lookup"><span data-stu-id="d3f75-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="d3f75-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3f75-123">Optional.</span></span> <span data-ttu-id="d3f75-124">Para exibir certificados para sua conta, repita as etapas de 3 a 6.</span><span class="sxs-lookup"><span data-stu-id="d3f75-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="d3f75-125">Na etapa 7, em vez de selecionar **conta de computador**, clique em **minha conta de usuário** e repita as etapas 8 a 10.</span><span class="sxs-lookup"><span data-stu-id="d3f75-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="d3f75-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3f75-126">Optional.</span></span> <span data-ttu-id="d3f75-127">Sobre o **arquivo** menu, clique em **salve** ou **Salvar como**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="d3f75-128">Salve o arquivo de console para reutilização posterior.</span><span class="sxs-lookup"><span data-stu-id="d3f75-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="d3f75-129">Exibindo certificados com o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="d3f75-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="d3f75-130">Você também pode exibir, exportar, importar e excluir certificados usando o Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d3f75-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="d3f75-131">Para exibir certificados com o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="d3f75-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="d3f75-132">No Internet Explorer, clique em **ferramentas**, em seguida, clique em **opções da Internet** para exibir o **opções da Internet** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d3f75-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="d3f75-133">Clique o **conteúdo** guia.</span><span class="sxs-lookup"><span data-stu-id="d3f75-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="d3f75-134">Sob **certificados**, clique em **certificados**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="d3f75-135">Para exibir detalhes de qualquer certificado, selecione o certificado e clique em **exibição**.</span><span class="sxs-lookup"><span data-stu-id="d3f75-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f75-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3f75-136">See also</span></span>
- [<span data-ttu-id="d3f75-137">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="d3f75-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d3f75-138">Como: Criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="d3f75-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="d3f75-139">Como: Recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="d3f75-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
