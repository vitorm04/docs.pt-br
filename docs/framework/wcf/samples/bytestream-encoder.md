---
title: Codificador ByteStream
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: ab9ccf47527dcf7f01f272f09b3b341d30fbd8d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="bytestream-encoder"></a><span data-ttu-id="544ed-102">Codificador ByteStream</span><span class="sxs-lookup"><span data-stu-id="544ed-102">ByteStream Encoder</span></span>
<span data-ttu-id="544ed-103">Este exemplo demonstra como criar um `ByteStreamHttpBinding`, um <xref:System.ServiceModel.Channels.Binding> que demonstra a funcionalidade do codificador de fluxo de bytes.</span><span class="sxs-lookup"><span data-stu-id="544ed-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="544ed-104">Discussão</span><span class="sxs-lookup"><span data-stu-id="544ed-104">Discussion</span></span>  
 <span data-ttu-id="544ed-105">Este exemplo demonstra como criar um padrão <xref:System.ServiceModel.Channels.Binding> usando os elementos de associação padrão <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="544ed-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="544ed-106">Este exemplo mostra como usar o codificador de fluxo de bytes para carregar e baixar uma imagem.</span><span class="sxs-lookup"><span data-stu-id="544ed-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="544ed-107">O recurso de codificador de fluxo de bytes suporta apenas o transporte HTTP e não dá suporte a recursos como o sistema de mensagens confiável ou segurança.</span><span class="sxs-lookup"><span data-stu-id="544ed-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="544ed-108">A única <xref:System.ServiceModel.Channels.MessageVersion> com suporte é <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="544ed-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="544ed-109">Se você estiver executando esse exemplo [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] ou [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], certifique-se de que você está executando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="544ed-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="544ed-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="544ed-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="544ed-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="544ed-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="544ed-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="544ed-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="544ed-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="544ed-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="544ed-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="544ed-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="544ed-115">Abra o arquivo ByteStreamHttpBinding.sln no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="544ed-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="544ed-116">Inicie uma nova instância do projeto ByteStreamHttpBindingServer clicando duas vezes no projeto no Gerenciador de soluções e selecionando **depurar**e, em seguida, **iniciar nova instância** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="544ed-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="544ed-117">Inicie uma nova instância do projeto ByteStreamHttpBindingClient clicando duas vezes no projeto no Gerenciador de soluções e selecionando **depurar**, **iniciar nova instância** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="544ed-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>
