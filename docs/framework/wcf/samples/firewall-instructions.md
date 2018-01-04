---
title: "Instruções do firewall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 270df09f709dfdfeb78b9bd72bc3744c6614bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="firewall-instructions"></a><span data-ttu-id="ea4aa-102">Instruções do firewall</span><span class="sxs-lookup"><span data-stu-id="ea4aa-102">Firewall Instructions</span></span>
<span data-ttu-id="ea4aa-103">Você deve habilitar várias portas ou programas no firewall para que o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemplos podem funcionar.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-103">You must enable several ports or programs in the firewall so that the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can function.</span></span> <span data-ttu-id="ea4aa-104">Muitos dos exemplos de se comunicar por meio de portas no intervalo de 8000-8003 e porta 9000.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="ea4aa-105">O firewall é ativado por padrão e impede o acesso a essas portas.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="ea4aa-106">Para habilitar o firewall para os exemplos, conclua um dos procedimentos a seguir, dependendo dos requisitos e o ambiente de segurança:</span><span class="sxs-lookup"><span data-stu-id="ea4aa-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="ea4aa-107">Opção 1: Habilite interativamente exemplos durante a execução.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="ea4aa-108">Não fizer nenhuma alteração antecipada para sua configuração de firewall e vá para iniciar a criação e executar os exemplos.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="ea4aa-109">Quando um exemplo é executado, uma **alerta de segurança do Windows** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="ea4aa-110">O programa de exemplo em questão, em seguida, pode ser adicionado interativamente a uma lista desbloqueada.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="ea4aa-111">Com esse procedimento, você precisará reiniciar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="ea4aa-112">Opção 2: Habilitar os programas de exemplo com antecedência.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="ea4aa-113">Iniciar o **painel de controle do Windows Firewall** applet e habilitar o exemplo programas que deseja executar.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="ea4aa-114">Você deve criar os programas de primeiro para que os arquivos executáveis existem.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="ea4aa-115">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="ea4aa-116">Opção 3: Habilite um intervalo de portas com antecedência.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="ea4aa-117">Iniciar o **Firewall do Windows** **painel de controle** applet e habilitar portas 80, 443, 8000 8003 e 9000, que são usados pelos exemplos.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="ea4aa-118">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="ea4aa-119">Essa opção é menos segura do que os outros porque ele permite que qualquer programa usa essas portas, não apenas os exemplos.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="ea4aa-120">Se você não tiver certeza de qual procedimento para usar, escolha a primeira opção.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="ea4aa-121">Se você estiver executando um firewall de outro fornecedor, talvez seja necessário fazer alterações semelhantes.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ea4aa-122">Alterar sua configuração de firewall afeta sua segurança.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="ea4aa-123">É recomendável que você registre as alterações, verifique e removê-los quando tiver terminado de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="ea4aa-124">Para habilitar os programas de exemplos com antecedência</span><span class="sxs-lookup"><span data-stu-id="ea4aa-124">To enable samples programs in advance</span></span>  
  
1.  <span data-ttu-id="ea4aa-125">Crie o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-125">Build the sample.</span></span>  
  
2.  <span data-ttu-id="ea4aa-126">Clique em **iniciar**, clique em **executar**e o tipo `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="ea4aa-127">Isso abre o **painel de controle do Windows Firewall** miniaplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea4aa-128">Você deve ter permissão para alterar as configurações de Firewall para executar os exemplos que exigem a capacidade de se comunicar através do Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="ea4aa-129">Se algumas configurações do firewall não estão disponíveis e o computador está conectado a um domínio, o administrador do sistema talvez esteja controlando essas configurações por meio da política de grupo.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3.  <span data-ttu-id="ea4aa-130">Conclua uma das seguintes etapas específicas operacionais para permitir um programa pelo Firewall do Windows:</span><span class="sxs-lookup"><span data-stu-id="ea4aa-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="ea4aa-131">No Windows 7 ou Windows Server 2008 r2, clique em **permitir um programa ou recurso pelo Firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="ea4aa-132">Clique em **alterar configurações**, permitir **outro programa...** .</span><span class="sxs-lookup"><span data-stu-id="ea4aa-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="ea4aa-133">Em [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], clique em **permitir um programa pelo Firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4.  <span data-ttu-id="ea4aa-134">Sobre o **exceções** , clique em **adicionar programa**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5.  <span data-ttu-id="ea4aa-135">Clique o **procurar** botão e selecione o arquivo executável do exemplo que você pretende executar.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6.  <span data-ttu-id="ea4aa-136">Repita as etapas 4 e 5 até que você adicionou os arquivos executáveis de todos os exemplos que você pretende executar.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7.  <span data-ttu-id="ea4aa-137">Clique em **Okey** para fechar o miniaplicativo de firewall.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="ea4aa-138">Para habilitar um intervalo de portas com antecedência</span><span class="sxs-lookup"><span data-stu-id="ea4aa-138">To enable a port range in advance</span></span>  
  
1.  <span data-ttu-id="ea4aa-139">Clique em **iniciar**, clique em **executar**e o tipo `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="ea4aa-140">Isso abre o **painel de controle do Windows Firewall** miniaplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2.  <span data-ttu-id="ea4aa-141">No Windows 7 ou Windows Server 2008 R2, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="ea4aa-142">Clique em **configurações avançadas** na coluna esquerda da janela do Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="ea4aa-143">Clique em **regras de entrada** na coluna esquerda.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="ea4aa-144">Clique em **novas regras** na coluna à direita.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="ea4aa-145">Selecione **porta** e clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="ea4aa-146">Selecione **TCP** e digite `8000, 8001, 8002, 8003, 9000, 80, 443` no **portas locais específicas** campo.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="ea4aa-147">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="ea4aa-148">Selecione **permitir a conexão**e clique em **próximo** .</span><span class="sxs-lookup"><span data-stu-id="ea4aa-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="ea4aa-149">Selecione **domínio** e **privada**e clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="ea4aa-150">Nomeie essa regra `WCF-WF 4.0 Samples`e clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="ea4aa-151">Clique em **as regras de saída** e repita as etapas de c m.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3.  <span data-ttu-id="ea4aa-152">Em [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="ea4aa-153">Clique em **permitir um programa pelo Firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="ea4aa-154">Sobre o **exceções** , clique em **adicionar porta**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="ea4aa-155">Insira um nome, digite 8000 como o número da porta e selecione o **TCP** opção.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="ea4aa-156">Clique o **Alterar escopo** botão, selecione o **minha rede** opção única (sub-rede) e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="ea4aa-157">Repita as etapas de b a d para portas 8001, 8002, 8003, 9000, 80 e 443.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4.  <span data-ttu-id="ea4aa-158">Clique em **Okey** para fechar o miniaplicativo de firewall.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea4aa-159">Remova as exceções de firewall quando tiver terminado de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="ea4aa-160">Para fazer isso, abra o **painel de controle do Windows Firewall** miniaplicativo e remova todos os programas ou porta entradas que foram adicionadas por procedimentos anteriores.</span><span class="sxs-lookup"><span data-stu-id="ea4aa-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
