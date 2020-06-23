---
title: Instalando o Enfileiramento de Mensagens (MSMQ)
description: Saiba como instalar o enfileiramento de mensagens 4,0 e o enfileiramento de mensagens 3,0 para usar os exemplos do WFC como parte de um procedimento de instalação única.
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 0d0cb87b40b1cb11eb7692c2fa1e890ec815b13d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244459"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="a1aee-103">Instalando o Enfileiramento de Mensagens (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="a1aee-103">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="a1aee-104">Os procedimentos a seguir mostram como instalar o Enfileiramento de Mensagens 4.0 e o Enfileiramento de Mensagens 3.0.</span><span class="sxs-lookup"><span data-stu-id="a1aee-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1aee-105">O enfileiramento de mensagens 4,0 não está disponível no Windows XP e no Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="a1aee-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="a1aee-106">Para instalar o Enfileiramento de Mensagens 4.0 no Windows Server 2008 ou no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a1aee-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="a1aee-107">Em Gerenciador do Servidor, clique em **recursos**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="a1aee-108">No painel direito, em resumo de **recursos**, clique em **Adicionar recursos**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="a1aee-109">Na janela resultante, expanda **enfileiramento de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="a1aee-110">Expanda **serviços de enfileiramento de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="a1aee-111">Clique em **integração de serviços de diretório** (para computadores ingressados em um domínio) e clique em **suporte http**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="a1aee-112">Clique em **Avançar**e em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="a1aee-113">Para instalar o Enfileiramento de Mensagens 4.0 no Windows 7 ou no Windows Vista</span><span class="sxs-lookup"><span data-stu-id="a1aee-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="a1aee-114">Abra o **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="a1aee-115">Clique em **programas** e, em **programas e recursos**, clique em **ativar e desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="a1aee-116">Expanda o Servidor Fila MSMQ, expanda o Server Core Fila MSMQ e marque as caixas de seleção dos seguintes recursos do Enfileiramento de Mensagens a serem instalados:</span><span class="sxs-lookup"><span data-stu-id="a1aee-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="a1aee-117">Integração de MSMQ com os Serviços de Domínio Active Directory (para computadores ingressos em um Domínio).</span><span class="sxs-lookup"><span data-stu-id="a1aee-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="a1aee-118">Suporte a HTTP do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a1aee-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="a1aee-119">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="a1aee-120">Se for solicitado que você reinicie o computador, clique em **OK** para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="a1aee-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="a1aee-121">Para instalar o Enfileiramento de Mensagens 3.0 no Windows XP e no Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="a1aee-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="a1aee-122">Abra o **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="a1aee-123">Clique em **Adicionar remover programas** e, em seguida, clique em **adicionar componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="a1aee-124">Selecione enfileiramento de mensagens e clique em **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a1aee-125">Se você estiver executando o Windows Server 2003, selecione servidor de aplicativos para acessar o enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a1aee-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="a1aee-126">Verifique se a opção Suporte a HTTP do MSMQ está selecionada na página de detalhes.</span><span class="sxs-lookup"><span data-stu-id="a1aee-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="a1aee-127">Clique em **OK** para sair da página de detalhes e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a1aee-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="a1aee-128">Conclua a instalação.</span><span class="sxs-lookup"><span data-stu-id="a1aee-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="a1aee-129">Se for solicitado que você reinicie o computador, clique em **OK** para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="a1aee-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1aee-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="a1aee-130">See also</span></span>

- [<span data-ttu-id="a1aee-131">Instruções de configuração</span><span class="sxs-lookup"><span data-stu-id="a1aee-131">Set-Up Instructions</span></span>](set-up-instructions.md)
