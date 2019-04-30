---
title: 'Como: Exibir certificados com o snap-in do MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972701"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="f41d6-102">Como: Exibir certificados com o snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="f41d6-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="f41d6-103">Quando você cria um cliente seguro ou serviço, você pode usar um [certificado](working-with-certificates.md) como a credencial.</span><span class="sxs-lookup"><span data-stu-id="f41d6-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="f41d6-104">Por exemplo, um tipo comum de credencial é o certificado X.509, que você criar com o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="f41d6-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span> 

<span data-ttu-id="f41d6-105">Há três tipos diferentes de repositórios de certificados que você pode examinar com o Microsoft Management Console (MMC) em sistemas Windows:</span><span class="sxs-lookup"><span data-stu-id="f41d6-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="f41d6-106">Computador local: O armazenamento é global para todos os usuários no dispositivo e local para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f41d6-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="f41d6-107">Usuário atual: O armazenamento é local para a conta de usuário atual no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f41d6-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="f41d6-108">Conta de serviço: O armazenamento é local para um serviço específico no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f41d6-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="f41d6-109">Exibir certificados no snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="f41d6-109">View certificates in the MMC snap-in</span></span> 

<span data-ttu-id="f41d6-110">O procedimento a seguir demonstra como examinar os repositórios em seu dispositivo local para localizar um certificado apropriado:</span><span class="sxs-lookup"><span data-stu-id="f41d6-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span> 
  
1. <span data-ttu-id="f41d6-111">Selecione **executados** da **inicie** menu e, em seguida, insira *mmc*.</span><span class="sxs-lookup"><span data-stu-id="f41d6-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span> 

    <span data-ttu-id="f41d6-112">O MMC é exibida.</span><span class="sxs-lookup"><span data-stu-id="f41d6-112">The MMC appears.</span></span> 
  
2. <span data-ttu-id="f41d6-113">Dos **arquivo** menu, selecione **Adicionar/Remover Snap-In do**.</span><span class="sxs-lookup"><span data-stu-id="f41d6-113">From the **File** menu, select **Add/Remove Snap In**.</span></span> 
    
    <span data-ttu-id="f41d6-114">O **adicionar ou Remover Snap-ins** janela é exibida.</span><span class="sxs-lookup"><span data-stu-id="f41d6-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="f41d6-115">Dos **snap-ins disponíveis** , escolha **certificados**, em seguida, selecione **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f41d6-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Adicionar snap-in de certificado](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="f41d6-117">No **snap-in de certificados** janela, selecione **conta de computador**e, em seguida, selecione **próxima**.</span><span class="sxs-lookup"><span data-stu-id="f41d6-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span> 
  
    <span data-ttu-id="f41d6-118">Opcionalmente, você pode selecionar **minha conta de usuário** para o usuário atual ou **conta de serviço** para um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="f41d6-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="f41d6-119">Se você não for um administrador para seu dispositivo, você pode gerenciar certificados somente para sua conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="f41d6-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="f41d6-120">No **Selecionar computador** janela, deixe **computador Local** selecionado e, em seguida, selecione **concluir**.</span><span class="sxs-lookup"><span data-stu-id="f41d6-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="f41d6-121">No **adicionar ou Remover Snap-in** janela, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="f41d6-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Adicionar snap-in de certificado](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="f41d6-123">Opcionais: Dos **arquivo** menu, selecione **salve** ou **Salvar como** para salvar o arquivo de console do MMC para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="f41d6-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="f41d6-124">Para exibir os certificados no snap-in do MMC, selecione **raiz do Console** no painel esquerdo, expanda **certificados (computador Local)**.</span><span class="sxs-lookup"><span data-stu-id="f41d6-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="f41d6-125">É exibida uma lista de diretórios para cada tipo de certificado.</span><span class="sxs-lookup"><span data-stu-id="f41d6-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="f41d6-126">Cada diretório de certificado, você pode exibir, exportar, importar e excluir seus certificados.</span><span class="sxs-lookup"><span data-stu-id="f41d6-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="f41d6-127">Exibir certificados com a ferramenta de Gerenciador de certificados</span><span class="sxs-lookup"><span data-stu-id="f41d6-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="f41d6-128">Você também pode exibir, exportar, importar e excluir certificados usando a ferramenta de Gerenciador de certificados.</span><span class="sxs-lookup"><span data-stu-id="f41d6-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="f41d6-129">Para exibir certificados para o dispositivo local</span><span class="sxs-lookup"><span data-stu-id="f41d6-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="f41d6-130">Selecione **executados** da **inicie** menu e, em seguida, insira *certlm*.</span><span class="sxs-lookup"><span data-stu-id="f41d6-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span> 

    <span data-ttu-id="f41d6-131">A ferramenta de Gerenciador de certificados para o dispositivo local é exibido.</span><span class="sxs-lookup"><span data-stu-id="f41d6-131">The Certificate Manager tool for the local device appears.</span></span> 
  
2. <span data-ttu-id="f41d6-132">Para exibir os certificados, em **certificados - computador Local** no painel esquerdo, expanda o diretório para o tipo de certificado que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="f41d6-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="f41d6-133">Para exibir certificados para o usuário atual</span><span class="sxs-lookup"><span data-stu-id="f41d6-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="f41d6-134">Selecione **executados** da **inicie** menu e, em seguida, insira *certmgr. msc*.</span><span class="sxs-lookup"><span data-stu-id="f41d6-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span> 

    <span data-ttu-id="f41d6-135">A ferramenta de Gerenciador de certificados para o usuário atual é exibida.</span><span class="sxs-lookup"><span data-stu-id="f41d6-135">The Certificate Manager tool for the current user appears.</span></span> 
  
2. <span data-ttu-id="f41d6-136">Para exibir os certificados, em **certificados - usuário atual** no painel esquerdo, expanda o diretório para o tipo de certificado que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="f41d6-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="f41d6-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f41d6-137">See also</span></span>

- [<span data-ttu-id="f41d6-138">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="f41d6-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="f41d6-139">Como: Criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="f41d6-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="f41d6-140">Como: Recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="f41d6-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
