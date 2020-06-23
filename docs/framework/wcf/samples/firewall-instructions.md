---
title: Instruções do firewall
description: Saiba como habilitar portas ou programas no firewall para exemplos do WCF. Use um desses procedimentos, dependendo de seus requisitos e ambiente de segurança.
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: de55d067960b8f2096c129f6feaf037219e06a96
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246130"
---
# <a name="firewall-instructions"></a><span data-ttu-id="58830-104">Instruções de firewall</span><span class="sxs-lookup"><span data-stu-id="58830-104">Firewall instructions</span></span>

<span data-ttu-id="58830-105">Você deve habilitar várias portas ou programas no firewall para que os exemplos de Windows Communication Foundation (WCF) possam funcionar.</span><span class="sxs-lookup"><span data-stu-id="58830-105">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="58830-106">Muitos dos exemplos se comunicam usando portas no intervalo de 8000-8003 e a porta 9000.</span><span class="sxs-lookup"><span data-stu-id="58830-106">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="58830-107">O firewall é ativado por padrão e impede o acesso a essas portas.</span><span class="sxs-lookup"><span data-stu-id="58830-107">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="58830-108">Para habilitar o firewall para os exemplos, conclua um dos seguintes procedimentos, dependendo de seus requisitos e ambiente de segurança:</span><span class="sxs-lookup"><span data-stu-id="58830-108">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>

- <span data-ttu-id="58830-109">Opção 1: habilitar os exemplos interativamente durante a execução.</span><span class="sxs-lookup"><span data-stu-id="58830-109">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="58830-110">Não faça nenhuma alteração antecipada na configuração do firewall e continue para começar a criar e executar os exemplos.</span><span class="sxs-lookup"><span data-stu-id="58830-110">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="58830-111">Quando um exemplo é executado, uma caixa de diálogo **alerta de segurança do Windows** é exibida.</span><span class="sxs-lookup"><span data-stu-id="58830-111">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="58830-112">O programa de exemplo em questão pode ser adicionado interativamente a uma lista desbloqueada.</span><span class="sxs-lookup"><span data-stu-id="58830-112">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="58830-113">Com esse procedimento, talvez seja necessário reiniciar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="58830-113">With this procedure, you may have to then restart the sample.</span></span>

- <span data-ttu-id="58830-114">Opção 2: habilite os programas de exemplo com antecedência.</span><span class="sxs-lookup"><span data-stu-id="58830-114">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="58830-115">Inicie o miniaplicativo do **painel de controle do firewall do Windows** e habilite os programas de exemplo que você planeja executar.</span><span class="sxs-lookup"><span data-stu-id="58830-115">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="58830-116">Você deve criar os programas primeiro para que os arquivos executáveis existam.</span><span class="sxs-lookup"><span data-stu-id="58830-116">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="58830-117">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="58830-117">You can find more detailed instructions in the following procedure.</span></span>

- <span data-ttu-id="58830-118">Opção 3: habilitar um intervalo de portas com antecedência.</span><span class="sxs-lookup"><span data-stu-id="58830-118">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="58830-119">Inicie o miniaplicativo do **painel de controle do firewall do Windows** e habilite as portas 80, 443, 8000-8003 e 9000, que são usadas pelos exemplos.</span><span class="sxs-lookup"><span data-stu-id="58830-119">Start the **Windows Firewall Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="58830-120">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="58830-120">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="58830-121">Essa opção é menos segura do que as outras porque permite que qualquer programa use essas portas, não apenas os exemplos.</span><span class="sxs-lookup"><span data-stu-id="58830-121">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>

<span data-ttu-id="58830-122">Se você não tiver certeza de qual procedimento usar, escolha a primeira opção.</span><span class="sxs-lookup"><span data-stu-id="58830-122">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="58830-123">Se você estiver executando um firewall de outro fornecedor, talvez seja necessário fazer alterações semelhantes.</span><span class="sxs-lookup"><span data-stu-id="58830-123">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58830-124">A alteração da configuração do firewall afeta sua segurança.</span><span class="sxs-lookup"><span data-stu-id="58830-124">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="58830-125">É recomendável que você registre as alterações feitas e remova-as quando terminar de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="58830-125">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>

## <a name="enable-samples-programs-in-advance"></a><span data-ttu-id="58830-126">Habilitar programas de exemplo com antecedência</span><span class="sxs-lookup"><span data-stu-id="58830-126">Enable samples programs in advance</span></span>

1. <span data-ttu-id="58830-127">Compile o exemplo.</span><span class="sxs-lookup"><span data-stu-id="58830-127">Build the sample.</span></span>

2. <span data-ttu-id="58830-128">Escolha **Iniciar**  >  **execução**e digite `firewall.cpl` .</span><span class="sxs-lookup"><span data-stu-id="58830-128">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="58830-129">Isso abre o miniaplicativo do **painel de controle do firewall do Windows** .</span><span class="sxs-lookup"><span data-stu-id="58830-129">This opens the **Windows Firewall Control Panel** applet.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58830-130">Você deve ter permissão para alterar as configurações de firewall para executar exemplos que exigem a capacidade de comunicação por meio do firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="58830-130">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="58830-131">Se algumas configurações de firewall estiverem indisponíveis e o computador estiver conectado a um domínio, o administrador do sistema poderá estar controlando essas configurações por meio de Política de Grupo.</span><span class="sxs-lookup"><span data-stu-id="58830-131">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>

3. <span data-ttu-id="58830-132">Conclua uma das seguintes etapas específicas de operação para permitir um programa por meio do firewall do Windows:</span><span class="sxs-lookup"><span data-stu-id="58830-132">Complete one of the following operating-specific steps to allow a program through the Windows Firewall:</span></span>

    - <span data-ttu-id="58830-133">No Windows 7 ou no Windows Server 2008 R2, clique em **permitir um programa ou recurso pelo firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="58830-133">On Windows 7 or Windows Server 2008 R2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="58830-134">Clique em **alterar configurações**  >  **permitir outro programa**.</span><span class="sxs-lookup"><span data-stu-id="58830-134">Click **Change Settings** > **Allow Another Program**.</span></span>

    - <span data-ttu-id="58830-135">No Windows Vista ou no Windows Server 2008, clique em **permitir um programa pelo firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="58830-135">On Windows Vista or Windows Server 2008, click **Allow a program through Windows Firewall**.</span></span>

4. <span data-ttu-id="58830-136">Na guia **exceções** , clique em **Adicionar programa**.</span><span class="sxs-lookup"><span data-stu-id="58830-136">On the **Exceptions** tab, click **Add Program**.</span></span>

5. <span data-ttu-id="58830-137">Clique no botão **procurar** e selecione o arquivo executável do exemplo que você planeja executar.</span><span class="sxs-lookup"><span data-stu-id="58830-137">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>

6. <span data-ttu-id="58830-138">Repita as etapas 4 e 5 até adicionar os arquivos executáveis de todos os exemplos que você planeja executar.</span><span class="sxs-lookup"><span data-stu-id="58830-138">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>

7. <span data-ttu-id="58830-139">Clique em **OK** para fechar o miniaplicativo firewall.</span><span class="sxs-lookup"><span data-stu-id="58830-139">Click **OK** to close the firewall applet.</span></span>

## <a name="enable-a-port-range-in-advance"></a><span data-ttu-id="58830-140">Habilitar um intervalo de portas com antecedência</span><span class="sxs-lookup"><span data-stu-id="58830-140">Enable a port range in advance</span></span>

1. <span data-ttu-id="58830-141">Escolha **Iniciar**  >  **execução**e digite `firewall.cpl` .</span><span class="sxs-lookup"><span data-stu-id="58830-141">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="58830-142">Isso abre o miniaplicativo do **painel de controle do firewall do Windows** .</span><span class="sxs-lookup"><span data-stu-id="58830-142">This opens the **Windows Firewall Control Panel** applet.</span></span>

2. <span data-ttu-id="58830-143">No Windows 7 ou no Windows Server 2008 R2, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="58830-143">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>

    1. <span data-ttu-id="58830-144">Clique em **Configurações avançadas** na coluna esquerda da janela Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="58830-144">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>

    2. <span data-ttu-id="58830-145">Clique em **regras de entrada** na coluna esquerda.</span><span class="sxs-lookup"><span data-stu-id="58830-145">Click **Inbound Rules** in the left column.</span></span>

    3. <span data-ttu-id="58830-146">Clique em **novas regras** na coluna à direita.</span><span class="sxs-lookup"><span data-stu-id="58830-146">Click **New Rules** in the right column.</span></span>

    4. <span data-ttu-id="58830-147">Selecione **porta** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="58830-147">Select **Port** and click **next**.</span></span>

    5. <span data-ttu-id="58830-148">Selecione **TCP** e insira `8000, 8001, 8002, 8003, 9000, 80, 443` no campo **portas locais específicas** .</span><span class="sxs-lookup"><span data-stu-id="58830-148">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>

    6. <span data-ttu-id="58830-149">Clique em **Próximo**.</span><span class="sxs-lookup"><span data-stu-id="58830-149">Click **Next**.</span></span>

    7. <span data-ttu-id="58830-150">Selecione **permitir a conexão**e clique em **Avançar** .</span><span class="sxs-lookup"><span data-stu-id="58830-150">Select **Allow the connection**, and click **Next** .</span></span>

    8. <span data-ttu-id="58830-151">Selecione **domínio** e **privado**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="58830-151">Select **Domain** and **Private**, and click **Next**.</span></span>

    9. <span data-ttu-id="58830-152">Nomeie essa regra `WCF-WF 4.0 Samples` e clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="58830-152">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>

    10. <span data-ttu-id="58830-153">Clique em **regras de saída** e repita as etapas de c a h.</span><span class="sxs-lookup"><span data-stu-id="58830-153">Click **Outbound Rules** and repeat steps c to h.</span></span>

3. <span data-ttu-id="58830-154">No Windows Vista ou no Windows Server 2008, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="58830-154">On Windows Vista or Windows Server 2008, follow these steps.</span></span>

    1. <span data-ttu-id="58830-155">Clique em **Permitir um programa pelo Firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="58830-155">Click **Allow a program through Windows Firewall**.</span></span>

    2. <span data-ttu-id="58830-156">Na guia **exceções** , clique em **Adicionar porta**.</span><span class="sxs-lookup"><span data-stu-id="58830-156">On the **Exceptions** tab, click **Add Port**.</span></span>

    3. <span data-ttu-id="58830-157">Insira um nome, insira 8000 como o número da porta e selecione a opção **TCP** .</span><span class="sxs-lookup"><span data-stu-id="58830-157">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>

    4. <span data-ttu-id="58830-158">Clique no botão **alterar escopo** , selecione a opção **minha rede** (sub-rede) somente e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="58830-158">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>

    5. <span data-ttu-id="58830-159">Repita as etapas de b a d para as portas 8001, 8002, 8003, 9000, 80 e 443.</span><span class="sxs-lookup"><span data-stu-id="58830-159">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>

4. <span data-ttu-id="58830-160">Clique em **OK** para fechar o miniaplicativo firewall.</span><span class="sxs-lookup"><span data-stu-id="58830-160">Click **OK** to close the firewall applet.</span></span>

> [!NOTE]
> <span data-ttu-id="58830-161">Remova as exceções de firewall quando terminar de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="58830-161">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="58830-162">Para fazer isso, abra o miniaplicativo do **painel de controle do firewall do Windows** e remova todos os programas ou entradas de porta que foram adicionados pelos procedimentos anteriores.</span><span class="sxs-lookup"><span data-stu-id="58830-162">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
