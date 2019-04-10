---
title: Instalando o Enfileiramento de Mensagens (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 64736f8f0a34a53658dd2838738a3d36b3891d2d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305085"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="3f624-102">Instalando o Enfileiramento de Mensagens (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="3f624-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="3f624-103">Os procedimentos a seguir mostram como instalar o Enfileiramento de Mensagens 4.0 e o Enfileiramento de Mensagens 3.0.</span><span class="sxs-lookup"><span data-stu-id="3f624-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f624-104">O Enfileiramento de Mensagens 4.0 não está disponível no [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nem no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f624-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="3f624-105">Para instalar o Enfileiramento de Mensagens 4.0 no Windows Server 2008 ou no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="3f624-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="3f624-106">No Gerenciador do servidor, clique em **recursos**.</span><span class="sxs-lookup"><span data-stu-id="3f624-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="3f624-107">No painel direito, sob **resumo de recursos**, clique em **adicionar recursos**.</span><span class="sxs-lookup"><span data-stu-id="3f624-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="3f624-108">Na janela resultante, expanda **enfileiramento**.</span><span class="sxs-lookup"><span data-stu-id="3f624-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="3f624-109">Expandir **serviços de enfileiramento de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="3f624-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="3f624-110">Clique em **integração de serviços de diretório** (para computadores que ingressaram em um domínio), em seguida, clique em **suporte HTTP**.</span><span class="sxs-lookup"><span data-stu-id="3f624-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="3f624-111">Clique em **próxima**, em seguida, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="3f624-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="3f624-112">Para instalar o Enfileiramento de Mensagens 4.0 no Windows 7 ou no Windows Vista</span><span class="sxs-lookup"><span data-stu-id="3f624-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="3f624-113">Abra **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="3f624-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="3f624-114">Clique em **programas** e, em **programas e recursos**, clique em **ativar e desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="3f624-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="3f624-115">Expanda o Servidor Fila MSMQ, expanda o Server Core Fila MSMQ e marque as caixas de seleção dos seguintes recursos do Enfileiramento de Mensagens a serem instalados:</span><span class="sxs-lookup"><span data-stu-id="3f624-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    -   <span data-ttu-id="3f624-116">Integração de MSMQ com os Serviços de Domínio Active Directory (para computadores ingressos em um Domínio).</span><span class="sxs-lookup"><span data-stu-id="3f624-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    -   <span data-ttu-id="3f624-117">Suporte a HTTP do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3f624-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="3f624-118">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="3f624-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="3f624-119">Se você for solicitado a reiniciar o computador, clique em **Okey** para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="3f624-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="3f624-120">Para instalar o Enfileiramento de Mensagens 3.0 no Windows XP e no Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="3f624-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="3f624-121">Abra **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="3f624-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="3f624-122">Clique em **adicionar ou remover programas** e, em seguida, clique em **adicionar componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="3f624-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="3f624-123">Selecione enfileiramento de mensagens e clique em **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="3f624-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3f624-124">Se você estiver executando o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], selecione Servidor de Aplicativos para acessar o Enfileiramento de Mensagens.</span><span class="sxs-lookup"><span data-stu-id="3f624-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="3f624-125">Verifique se a opção Suporte a HTTP do MSMQ está selecionada na página de detalhes.</span><span class="sxs-lookup"><span data-stu-id="3f624-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="3f624-126">Clique em **Okey** para sair da página de detalhes e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="3f624-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="3f624-127">Conclua a instalação.</span><span class="sxs-lookup"><span data-stu-id="3f624-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="3f624-128">Se você for solicitado a reiniciar o computador, clique em **Okey** para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="3f624-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f624-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f624-129">See also</span></span>

- [<span data-ttu-id="3f624-130">Instruções de configuração</span><span class="sxs-lookup"><span data-stu-id="3f624-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
