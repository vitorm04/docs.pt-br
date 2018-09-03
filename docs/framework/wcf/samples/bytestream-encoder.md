---
title: Codificador ByteStream
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: cbd4110ecc04923b79d6b910fcf7ab4ca2012680
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480686"
---
# <a name="bytestream-encoder"></a>Codificador ByteStream
Este exemplo demonstra como criar uma `ByteStreamHttpBinding`, um <xref:System.ServiceModel.Channels.Binding> que demonstra a funcionalidade do codificador de fluxo de bytes.  
  
## <a name="discussion"></a>Discussão  
 Este exemplo demonstra como criar um padrão <xref:System.ServiceModel.Channels.Binding> usando os elementos de associação padrão <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.HttpTransportBindingElement>. Este exemplo mostra como usar o codificador de fluxo de bytes para carregar e baixar uma imagem. O recurso de codificador de fluxo de bytes apenas suporta o transporte HTTP e não oferece suporte a recursos como o sistema de mensagens confiável ou segurança. As únicas <xref:System.ServiceModel.Channels.MessageVersion> com suporte é <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Se você estiver executando este exemplo [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] ou [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], certifique-se de que você está executando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] com privilégios elevados.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o arquivo ByteStreamHttpBinding.sln no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Iniciar uma nova instância do projeto ByteStreamHttpBindingServer clicando com botão direito no projeto no Gerenciador de soluções e selecionando **Debug**e então **iniciar nova instância** no menu de contexto.  
  
3.  Iniciar uma nova instância do projeto ByteStreamHttpBindingClient clicando com botão direito no projeto no Gerenciador de soluções e selecionando **Debug**, **iniciar nova instância** no menu de contexto.
