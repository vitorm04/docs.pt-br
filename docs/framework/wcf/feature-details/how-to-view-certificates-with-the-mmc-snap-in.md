---
title: Como exibir certificados com o snap-in do MMC
description: Um cliente ou serviço WCF seguro pode usar um certificado como uma credencial. Saiba mais sobre os tipos de repositórios de certificados que você pode examinar usando o plug-in do MMC.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246669"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="54922-104">Como exibir certificados com o snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="54922-104">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="54922-105">Ao criar um cliente ou serviço seguro, você pode usar um [certificado](working-with-certificates.md) como a credencial.</span><span class="sxs-lookup"><span data-stu-id="54922-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="54922-106">Por exemplo, um tipo comum de credencial é o certificado X. 509, que você cria com o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="54922-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="54922-107">Há três tipos diferentes de repositórios de certificados que você pode examinar com o MMC (console de gerenciamento Microsoft) em sistemas Windows:</span><span class="sxs-lookup"><span data-stu-id="54922-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="54922-108">Computador local: o repositório é local para o dispositivo e global para todos os usuários no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="54922-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="54922-109">Usuário atual: o repositório é local para a conta de usuário atual no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="54922-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="54922-110">Conta de serviço: o repositório é local para um serviço específico no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="54922-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="54922-111">Exibir certificados no snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="54922-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="54922-112">O procedimento a seguir demonstra como examinar as lojas em seu dispositivo local para encontrar um certificado apropriado:</span><span class="sxs-lookup"><span data-stu-id="54922-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="54922-113">Selecione **executar** no menu **Iniciar** e, em seguida, insira *MMC*.</span><span class="sxs-lookup"><span data-stu-id="54922-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="54922-114">O MMC é exibido.</span><span class="sxs-lookup"><span data-stu-id="54922-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="54922-115">No menu **arquivo** , selecione **Adicionar/remover snap-in**.</span><span class="sxs-lookup"><span data-stu-id="54922-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="54922-116">A janela **Adicionar ou remover snap-ins** é exibida.</span><span class="sxs-lookup"><span data-stu-id="54922-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="54922-117">Na lista **snap-ins disponíveis** , escolha **certificados**e, em seguida, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="54922-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Adicionar Snap-in de certificado](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="54922-119">Na janela **snap-in de certificados** , selecione **conta de computador**e, em seguida, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="54922-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="54922-120">Opcionalmente, você pode selecionar **minha conta de usuário** para o usuário atual ou a **conta de serviço** para um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="54922-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="54922-121">Se você não for um administrador para seu dispositivo, poderá gerenciar certificados somente para sua conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="54922-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="54922-122">Na janela **Selecionar computador** , deixe **computador local** selecionado e, em seguida, selecione **concluir**.</span><span class="sxs-lookup"><span data-stu-id="54922-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="54922-123">Na janela **Adicionar ou remover snap-in** , selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="54922-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Adicionar Snap-in de certificado](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="54922-125">Opcional: no menu **arquivo** , selecione **salvar** ou **salvar como** para salvar o arquivo de console do MMC para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="54922-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="54922-126">Para exibir seus certificados no snap-in do MMC, selecione **raiz do console** no painel esquerdo e, em seguida, expanda **certificados (computador local)**.</span><span class="sxs-lookup"><span data-stu-id="54922-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="54922-127">Uma lista de diretórios para cada tipo de certificado é exibida.</span><span class="sxs-lookup"><span data-stu-id="54922-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="54922-128">Em cada diretório de certificado, você pode exibir, exportar, importar e excluir seus certificados.</span><span class="sxs-lookup"><span data-stu-id="54922-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="54922-129">Exibir certificados com a ferramenta Gerenciador de certificados</span><span class="sxs-lookup"><span data-stu-id="54922-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="54922-130">Você também pode exibir, exportar, importar e excluir certificados usando a ferramenta Gerenciador de certificados.</span><span class="sxs-lookup"><span data-stu-id="54922-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="54922-131">Para exibir certificados para o dispositivo local</span><span class="sxs-lookup"><span data-stu-id="54922-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="54922-132">Selecione **executar** no menu **Iniciar** e, em seguida, digite *certlm. msc*.</span><span class="sxs-lookup"><span data-stu-id="54922-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="54922-133">A ferramenta Gerenciador de certificados para o dispositivo local é exibida.</span><span class="sxs-lookup"><span data-stu-id="54922-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="54922-134">Para exibir seus certificados, em **certificados – computador local** no painel esquerdo, expanda o diretório do tipo de certificado que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="54922-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="54922-135">Para exibir certificados para o usuário atual</span><span class="sxs-lookup"><span data-stu-id="54922-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="54922-136">Selecione **executar** no menu **Iniciar** e digite *certmgr. msc*.</span><span class="sxs-lookup"><span data-stu-id="54922-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="54922-137">A ferramenta Gerenciador de certificados para o usuário atual é exibida.</span><span class="sxs-lookup"><span data-stu-id="54922-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="54922-138">Para exibir seus certificados, em **certificados – usuário atual** no painel esquerdo, expanda o diretório do tipo de certificado que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="54922-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="54922-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="54922-139">See also</span></span>

- [<span data-ttu-id="54922-140">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="54922-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="54922-141">Como criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="54922-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="54922-142">Como recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="54922-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
