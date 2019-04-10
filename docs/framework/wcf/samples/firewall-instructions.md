---
title: Instruções do firewall
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: f1b576b4e413fa3bae70ef1eb8f8ed768e28e309
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295153"
---
# <a name="firewall-instructions"></a><span data-ttu-id="3c2cd-102">Instruções do firewall</span><span class="sxs-lookup"><span data-stu-id="3c2cd-102">Firewall Instructions</span></span>
<span data-ttu-id="3c2cd-103">Você deve habilitar várias portas ou programas no firewall para que os exemplos do Windows Communication Foundation (WCF) podem funcionar.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="3c2cd-104">Muitos dos exemplos de se comunicar por meio de portas no intervalo 8000-8003 e porta 9000.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="3c2cd-105">O firewall está ativado por padrão e impede o acesso a essas portas.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="3c2cd-106">Para habilitar o firewall para os exemplos, conclua um dos procedimentos a seguir, dependendo de suas necessidades e ambiente de segurança:</span><span class="sxs-lookup"><span data-stu-id="3c2cd-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="3c2cd-107">Opção 1: Habilite interativamente amostras durante a execução.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="3c2cd-108">Não fazer nenhuma alteração de avanço em sua configuração de firewall e prossiga para começar a criar e executar os exemplos.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="3c2cd-109">Quando um exemplo é executado, uma **o alerta de segurança do Windows** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="3c2cd-110">O programa de exemplo em questão, em seguida, pode ser adicionado interativamente a uma lista desbloqueada.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="3c2cd-111">Com esse procedimento, você terá que reiniciar, em seguida, o exemplo.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="3c2cd-112">Opção 2: Habilite programas de exemplo com antecedência.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="3c2cd-113">Iniciar o **painel de controle do Windows Firewall** miniaplicativo e habilitar o exemplo de programas que deseja executar.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="3c2cd-114">Portanto, os arquivos executáveis existirem, você deve criar os programas de primeiro.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="3c2cd-115">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="3c2cd-116">Opção 3: Habilite um intervalo de portas com antecedência.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="3c2cd-117">Iniciar o **Firewall do Windows** **painel de controle** miniaplicativo e habilite as portas 80, 443, 8000 8003 e 9000, que são usados pelos exemplos.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="3c2cd-118">Você pode encontrar instruções mais detalhadas no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="3c2cd-119">Essa opção é menos segura do que os outros porque ele permite que qualquer programa usam essas portas, não apenas os exemplos.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="3c2cd-120">Se você não tiver certeza de qual procedimento para usar, escolha a primeira opção.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="3c2cd-121">Se você estiver executando um firewall de outro fornecedor, talvez você precise fazer alterações semelhantes.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c2cd-122">Alterar sua configuração de firewall afeta sua segurança.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="3c2cd-123">É recomendável que você registre as alterações que você fizer e removê-los quando tiver terminado de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="3c2cd-124">Para habilitar programas de exemplos com antecedência</span><span class="sxs-lookup"><span data-stu-id="3c2cd-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="3c2cd-125">Crie o exemplo.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="3c2cd-126">Clique em **inicie**, clique em **execute**e o tipo `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="3c2cd-127">Isso abre o **painel de controle do Windows Firewall** miniaplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c2cd-128">Você deve ter permissão para alterar as configurações de Firewall para executar os exemplos que exigem a capacidade de se comunicar através do Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="3c2cd-129">Se algumas configurações do firewall não estão disponíveis e o computador está conectado a um domínio, o administrador do sistema talvez esteja controlando essas configurações por meio de diretiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="3c2cd-130">Conclua uma das seguintes etapas específicas operacionais para permitir um programa pelo Firewall do Windows:</span><span class="sxs-lookup"><span data-stu-id="3c2cd-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="3c2cd-131">No Windows 7 ou Windows Server 2008 r2, clique em **permitem que um programa ou recurso pelo Firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="3c2cd-132">Clique em **alterar configurações**, permitir **outro programa...** .</span><span class="sxs-lookup"><span data-stu-id="3c2cd-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="3c2cd-133">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], clique em **permitir um programa pelo Firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="3c2cd-134">Sobre o **exceções** , clique em **adicionar programa**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="3c2cd-135">Clique o **procurar** botão e selecione o arquivo executável do exemplo que você pretende executar.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="3c2cd-136">Repita as etapas 4 e 5 até ter adicionado os arquivos executáveis de todos os exemplos que você pretende executar.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="3c2cd-137">Clique em **Okey** para fechar o miniaplicativo de firewall.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="3c2cd-138">Para habilitar um intervalo de portas com antecedência</span><span class="sxs-lookup"><span data-stu-id="3c2cd-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="3c2cd-139">Clique em **inicie**, clique em **execute**e o tipo `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="3c2cd-140">Isso abre o **painel de controle do Windows Firewall** miniaplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="3c2cd-141">No Windows 7 ou Windows Server 2008 R2, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="3c2cd-142">Clique em **configurações avançadas** na coluna esquerda da janela do Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="3c2cd-143">Clique em **regras de entrada** na coluna à esquerda.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="3c2cd-144">Clique em **novas regras** na coluna à direita.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="3c2cd-145">Selecione **porta** e clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="3c2cd-146">Selecione **TCP** e insira `8000, 8001, 8002, 8003, 9000, 80, 443` no **portas locais específicas** campo.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="3c2cd-147">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="3c2cd-148">Selecione **permitir a conexão**e clique em **próxima** .</span><span class="sxs-lookup"><span data-stu-id="3c2cd-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="3c2cd-149">Selecione **domínio** e **privada**e clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="3c2cd-150">Nomeie essa regra `WCF-WF 4.0 Samples`e clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="3c2cd-151">Clique em **regras de saída** e repita as etapas de c para h.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="3c2cd-152">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="3c2cd-153">Clique em **permitir um programa pelo Firewall do Windows**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="3c2cd-154">Sobre o **exceções** , clique em **adicionar porta**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="3c2cd-155">Insira um nome, digite 8000 como o número da porta e selecione o **TCP** opção.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="3c2cd-156">Clique o **Alterar escopo** botão, selecione o **minha rede** única opção de (sub-rede) e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="3c2cd-157">Repita as etapas de b a d para portas 8001, 8002, 8003, 9000, 80 e 443.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="3c2cd-158">Clique em **Okey** para fechar o miniaplicativo de firewall.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c2cd-159">Remova todas as exceções de firewall quando tiver terminado de trabalhar com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="3c2cd-160">Para fazer isso, abra o **painel de controle do Windows Firewall** miniaplicativo e remove nenhum programa ou porta entradas que foram adicionadas por procedimentos anteriores.</span><span class="sxs-lookup"><span data-stu-id="3c2cd-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
