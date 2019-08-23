---
title: Instruções do firewall
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 5e557963c415cf39c4f25b4854c9863652201146
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961400"
---
# <a name="firewall-instructions"></a><span data-ttu-id="55d06-102">Instruções do firewall</span><span class="sxs-lookup"><span data-stu-id="55d06-102">Firewall Instructions</span></span>
<span data-ttu-id="55d06-103">Você deve habilitar várias portas ou programas no firewall para que os exemplos de Windows Communication Foundation (WCF) possam funcionar.</span><span class="sxs-lookup"><span data-stu-id="55d06-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="55d06-104">Muitos dos exemplos se comunicam usando portas no intervalo de 8000-8003 e a porta 9000.</span><span class="sxs-lookup"><span data-stu-id="55d06-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="55d06-105">O firewall é ativado por padrão e impede o acesso a essas portas.</span><span class="sxs-lookup"><span data-stu-id="55d06-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="55d06-106">Para habilitar o firewall para os exemplos, conclua um dos seguintes procedimentos, dependendo de seus requisitos e ambiente de segurança:</span><span class="sxs-lookup"><span data-stu-id="55d06-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
- <span data-ttu-id="55d06-107">Opção 1: Habilite de modo interativo os exemplos durante a execução.</span><span class="sxs-lookup"><span data-stu-id="55d06-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="55d06-108">Não faça nenhuma alteração antecipada na configuração do firewall e continue para começar a criar e executar os exemplos.</span><span class="sxs-lookup"><span data-stu-id="55d06-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="55d06-109">Quando um exemplo é executado, uma caixa de diálogo **alerta de segurança do Windows** é exibida.</span><span class="sxs-lookup"><span data-stu-id="55d06-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="55d06-110">O programa de exemplo em questão pode ser adicionado interativamente a uma lista desbloqueada.</span><span class="sxs-lookup"><span data-stu-id="55d06-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="55d06-111">Com esse procedimento, talvez seja necessário reiniciar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="55d06-111">With this procedure, you may have to then restart the sample.</span></span>  
  
- <span data-ttu-id="55d06-112">Opção 2: Habilite os programas de exemplo com antecedência.</span><span class="sxs-lookup"><span data-stu-id="55d06-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="55d06-113">Inicie o miniaplicativo do **painel de controle do firewall do Windows** e habilite os programas de exemplo que você planeja executar.</span><span class="sxs-lookup"><span data-stu-id="55d06-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="55d06-114">Você deve criar os programas primeiro para que os arquivos executáveis existam.</span><span class="sxs-lookup"><span data-stu-id="55d06-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="55d06-115">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="55d06-115">You can find more detailed instructions in the following procedure.</span></span>  
  
- <span data-ttu-id="55d06-116">Opção 3: Habilite um intervalo de portas com antecedência.</span><span class="sxs-lookup"><span data-stu-id="55d06-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="55d06-117">Inicie o miniaplicativo do **painel de controle** do **Firewall do Windows** e habilite as portas 80, 443, 8000-8003 e 9000, que são usadas pelos exemplos.</span><span class="sxs-lookup"><span data-stu-id="55d06-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="55d06-118">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="55d06-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="55d06-119">Essa opção é menos segura do que as outras porque permite que qualquer programa use essas portas, não apenas os exemplos.</span><span class="sxs-lookup"><span data-stu-id="55d06-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="55d06-120">Se você não tiver certeza de qual procedimento usar, escolha a primeira opção.</span><span class="sxs-lookup"><span data-stu-id="55d06-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="55d06-121">Se você estiver executando um firewall de outro fornecedor, talvez seja necessário fazer alterações semelhantes.</span><span class="sxs-lookup"><span data-stu-id="55d06-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55d06-122">A alteração da configuração do firewall afeta sua segurança.</span><span class="sxs-lookup"><span data-stu-id="55d06-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="55d06-123">É recomendável que você registre as alterações feitas e remova-as quando terminar de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="55d06-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="55d06-124">Para habilitar os programas de exemplo com antecedência</span><span class="sxs-lookup"><span data-stu-id="55d06-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="55d06-125">Compile o exemplo.</span><span class="sxs-lookup"><span data-stu-id="55d06-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="55d06-126">Clique em **Iniciar**, **executar**e digite `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="55d06-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="55d06-127">Isso abre o miniaplicativo do **painel de controle do firewall do Windows** .</span><span class="sxs-lookup"><span data-stu-id="55d06-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55d06-128">Você deve ter permissão para alterar as configurações de firewall para executar exemplos que exigem a capacidade de comunicação por meio do firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="55d06-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="55d06-129">Se algumas configurações de firewall estiverem indisponíveis e o computador estiver conectado a um domínio, o administrador do sistema poderá estar controlando essas configurações por meio de Política de Grupo.</span><span class="sxs-lookup"><span data-stu-id="55d06-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="55d06-130">Conclua uma das seguintes etapas específicas de operação para permitir um programa por meio do firewall do Windows:</span><span class="sxs-lookup"><span data-stu-id="55d06-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    - <span data-ttu-id="55d06-131">No Windows 7 ou no Windows Server 2008 R2, clique em **permitir um programa ou recurso pelo firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="55d06-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="55d06-132">Clique em **alterar configurações**, permitir **outro programa...** .</span><span class="sxs-lookup"><span data-stu-id="55d06-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    - <span data-ttu-id="55d06-133">Em [!INCLUDE[wv](../../../../includes/wv-md.md)] ou[!INCLUDE[lserver](../../../../includes/lserver-md.md)], clique em **permitir um programa pelo firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="55d06-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="55d06-134">Na guia **exceções** , clique em **Adicionar programa**.</span><span class="sxs-lookup"><span data-stu-id="55d06-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="55d06-135">Clique no botão **procurar** e selecione o arquivo executável do exemplo que você planeja executar.</span><span class="sxs-lookup"><span data-stu-id="55d06-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="55d06-136">Repita as etapas 4 e 5 até adicionar os arquivos executáveis de todos os exemplos que você planeja executar.</span><span class="sxs-lookup"><span data-stu-id="55d06-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="55d06-137">Clique em **OK** para fechar o miniaplicativo firewall.</span><span class="sxs-lookup"><span data-stu-id="55d06-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="55d06-138">Para habilitar um intervalo de portas com antecedência</span><span class="sxs-lookup"><span data-stu-id="55d06-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="55d06-139">Clique em **Iniciar**, **executar**e digite `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="55d06-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="55d06-140">Isso abre o miniaplicativo do **painel de controle do firewall do Windows** .</span><span class="sxs-lookup"><span data-stu-id="55d06-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="55d06-141">No Windows 7 ou no Windows Server 2008 R2, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="55d06-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1. <span data-ttu-id="55d06-142">Clique em **Configurações avançadas** na coluna esquerda da janela Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="55d06-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2. <span data-ttu-id="55d06-143">Clique em **regras de entrada** na coluna esquerda.</span><span class="sxs-lookup"><span data-stu-id="55d06-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3. <span data-ttu-id="55d06-144">Clique em **novas regras** na coluna à direita.</span><span class="sxs-lookup"><span data-stu-id="55d06-144">Click **New Rules** in the right column.</span></span>  
  
    4. <span data-ttu-id="55d06-145">Selecione **porta** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="55d06-145">Select **Port** and click **next**.</span></span>  
  
    5. <span data-ttu-id="55d06-146">Selecione **TCP** e insira `8000, 8001, 8002, 8003, 9000, 80, 443` no campo **portas locais específicas** .</span><span class="sxs-lookup"><span data-stu-id="55d06-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6. <span data-ttu-id="55d06-147">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="55d06-147">Click **Next**.</span></span>  
  
    7. <span data-ttu-id="55d06-148">Selecione **permitir a conexão**e clique em **Avançar** .</span><span class="sxs-lookup"><span data-stu-id="55d06-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8. <span data-ttu-id="55d06-149">Selecione **domínio** e **privado**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="55d06-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="55d06-150">Nomeie essa regra `WCF-WF 4.0 Samples`e clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="55d06-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="55d06-151">Clique em **regras de saída** e repita as etapas de c a h.</span><span class="sxs-lookup"><span data-stu-id="55d06-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="55d06-152">No [!INCLUDE[wv](../../../../includes/wv-md.md)] ou[!INCLUDE[lserver](../../../../includes/lserver-md.md)], siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="55d06-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1. <span data-ttu-id="55d06-153">Clique em **permitir um programa pelo firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="55d06-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2. <span data-ttu-id="55d06-154">Na guia **exceções** , clique em **Adicionar porta**.</span><span class="sxs-lookup"><span data-stu-id="55d06-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3. <span data-ttu-id="55d06-155">Insira um nome, insira 8000 como o número da porta e selecione a opção **TCP** .</span><span class="sxs-lookup"><span data-stu-id="55d06-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4. <span data-ttu-id="55d06-156">Clique no botão **alterar escopo** , selecione a opção **minha rede** (sub-rede) somente e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="55d06-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5. <span data-ttu-id="55d06-157">Repita as etapas de b a d para as portas 8001, 8002, 8003, 9000, 80 e 443.</span><span class="sxs-lookup"><span data-stu-id="55d06-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="55d06-158">Clique em **OK** para fechar o miniaplicativo firewall.</span><span class="sxs-lookup"><span data-stu-id="55d06-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55d06-159">Remova as exceções de firewall quando terminar de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="55d06-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="55d06-160">Para fazer isso, abra o miniaplicativo do **painel de controle do firewall do Windows** e remova todos os programas ou entradas de porta que foram adicionados pelos procedimentos anteriores.</span><span class="sxs-lookup"><span data-stu-id="55d06-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
