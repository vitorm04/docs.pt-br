---
title: 'Como: Exibir certificados com o snap-in do MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184778"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="f5cac-102">Como: Exibir certificados com o snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="f5cac-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="f5cac-103">Quando você cria um cliente ou serviço seguro, você pode usar um [certificado](working-with-certificates.md) como credencial.</span><span class="sxs-lookup"><span data-stu-id="f5cac-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="f5cac-104">Por exemplo, um tipo comum de credencial é o certificado X.509, que você cria com o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="f5cac-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f5cac-105">Existem três tipos diferentes de lojas de certificados que você pode examinar com o Microsoft Management Console (MMC) em sistemas Windows:</span><span class="sxs-lookup"><span data-stu-id="f5cac-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="f5cac-106">Computador local: A loja é local para o dispositivo e global para todos os usuários no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5cac-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="f5cac-107">Usuário atual: A loja é local para a conta de usuário atual no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5cac-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="f5cac-108">Conta de serviço: A loja é local para um determinado serviço no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5cac-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="f5cac-109">Exibir certificados no snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="f5cac-109">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="f5cac-110">O procedimento a seguir demonstra como examinar as lojas em seu dispositivo local para encontrar um certificado apropriado:</span><span class="sxs-lookup"><span data-stu-id="f5cac-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="f5cac-111">Selecione **Executar** no menu **Iniciar** e, em seguida, digite *mmc*.</span><span class="sxs-lookup"><span data-stu-id="f5cac-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="f5cac-112">O MMC aparece.</span><span class="sxs-lookup"><span data-stu-id="f5cac-112">The MMC appears.</span></span>
  
2. <span data-ttu-id="f5cac-113">No **menu Arquivo,** **selecione Adicionar/Remover encaixar**.</span><span class="sxs-lookup"><span data-stu-id="f5cac-113">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="f5cac-114">A **janela Adicionar ou Remover Snap-ins** é exibida.</span><span class="sxs-lookup"><span data-stu-id="f5cac-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="f5cac-115">Na **lista de snap-ins disponíveis,** escolha **Certificados**e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f5cac-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Adicionar snap-in de certificado](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="f5cac-117">Na janela **snap-in Certificados,** selecione **Conta de computador**e selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="f5cac-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="f5cac-118">Opcionalmente, você pode selecionar **Minha conta de usuário** para a conta de usuário atual ou **serviço** para um determinado serviço.</span><span class="sxs-lookup"><span data-stu-id="f5cac-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f5cac-119">Se você não é um administrador do seu dispositivo, você pode gerenciar certificados apenas para sua conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="f5cac-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="f5cac-120">Na **janela Selecionar computador,** deixe o **computador local** selecionado e, em seguida, selecione **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="f5cac-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="f5cac-121">Na **janela Adicionar ou Remover snap-in,** selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5cac-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Adicionar snap-in de certificado](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="f5cac-123">Opcional: No menu **Arquivo,** **selecione Salvar** ou **Salvar como** para salvar o arquivo do console MMC para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="f5cac-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="f5cac-124">Para exibir seus certificados no snap-in do MMC, selecione **'Raiz** de console' no painel esquerdo e expanda **Certificados (Computador Local)**.</span><span class="sxs-lookup"><span data-stu-id="f5cac-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="f5cac-125">Uma lista de diretórios para cada tipo de certificado é exibida.</span><span class="sxs-lookup"><span data-stu-id="f5cac-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="f5cac-126">A partir de cada diretório de certificados, você pode visualizar, exportar, importar e excluir seus certificados.</span><span class="sxs-lookup"><span data-stu-id="f5cac-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="f5cac-127">Exibir certificados com a ferramenta Gerenciador de certificados</span><span class="sxs-lookup"><span data-stu-id="f5cac-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="f5cac-128">Você também pode visualizar, exportar, importar e excluir certificados usando a ferramenta Gerenciador de certificados.</span><span class="sxs-lookup"><span data-stu-id="f5cac-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="f5cac-129">Para exibir certificados para o dispositivo local</span><span class="sxs-lookup"><span data-stu-id="f5cac-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="f5cac-130">Selecione **Executar** no menu **Iniciar** e, em seguida, *digite certlm.msc*.</span><span class="sxs-lookup"><span data-stu-id="f5cac-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="f5cac-131">A ferramenta Gerenciador de certificados para o dispositivo local é exibida.</span><span class="sxs-lookup"><span data-stu-id="f5cac-131">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="f5cac-132">Para visualizar seus certificados, em **Certificados - Computador local** no painel esquerdo, expanda o diretório para o tipo de certificado que deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="f5cac-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="f5cac-133">Para exibir certificados para o usuário atual</span><span class="sxs-lookup"><span data-stu-id="f5cac-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="f5cac-134">Selecione **Executar** no menu **Iniciar** e, em seguida, *digite certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="f5cac-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="f5cac-135">A ferramenta Gerenciador de certificados para o usuário atual é exibida.</span><span class="sxs-lookup"><span data-stu-id="f5cac-135">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="f5cac-136">Para visualizar seus certificados, em **Certificados - Usuário atual** no painel esquerdo, expanda o diretório para o tipo de certificado que deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="f5cac-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5cac-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5cac-137">See also</span></span>

- [<span data-ttu-id="f5cac-138">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="f5cac-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="f5cac-139">Como: Criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="f5cac-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="f5cac-140">Como: Recuperar a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="f5cac-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
