---
title: Serviço básico de HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: ec716b41efb3dde6e5afdb386d797e402d924b56
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045153"
---
# <a name="basic-http-service"></a>Serviço básico de HTTP

Este exemplo demonstra como implementar um serviço baseado em RPC baseado em HTTP – popularmente conhecido como serviço "POX" (XML antigo), usando o modelo de programação REST do Windows Communication Foundation (WCF). Este exemplo consiste em dois componentes: um serviço HTTP do WCF auto-hospedado (Service.cs) e um aplicativo de console (Program.cs) que cria o serviço e faz chamadas para ele.

## <a name="sample-details"></a>Detalhes de exemplo

O serviço WCF expõe 2 operações `EchoWithGet` e `EchoWithPost`, que retorna a cadeia de caracteres que foi passada como entrada.

A `EchoWithGet` operação é anotada <xref:System.ServiceModel.Web.WebGetAttribute>, o que indica que a operação processa solicitações `GET` http. Como o <xref:System.ServiceModel.Web.WebGetAttribute> não especifica explicitamente um <xref:System.UriTemplate>, a operação espera que a cadeia de caracteres de entrada seja passada usando um parâmetro de cadeia de `s`caracteres de consulta com o nome. Observe que o formato do URI que o serviço espera pode ser personalizado usando a <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> propriedade.

A `EchoWithPost` operação é anotada <xref:System.ServiceModel.Web.WebInvokeAttribute>, o que indica que não é uma `GET` operação (ela tem efeitos colaterais). Como o <xref:System.ServiceModel.Web.WebInvokeAttribute> não especifica explicitamente um `Method`, a operação processa solicitações HTTP `POST` que têm a cadeia de caracteres no corpo da solicitação (no formato XML, por exemplo). Observe que o método http e o formato do URI para a solicitação podem ser personalizados usando as <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> Propriedades e, <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> respectivamente.

O arquivo app. config configura o serviço WCF com um padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> que tem a <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> propriedade definida como `true`. Como resultado, a infraestrutura do WCF cria uma página de ajuda baseada em HTML `http://localhost:8000/Customers/help` automática no que fornece informações sobre como construir solicitações HTTP para o serviço e como consumir a resposta http do serviço.

Program.cs demonstra como uma fábrica de canais WCF pode ser usada para fazer chamadas para o serviço e as respostas de processo. Observe que essa é apenas uma maneira de acessar um serviço WCF. Também é possível acessar o serviço usando outras classes de .NET Framework como <xref:System.Net.HttpWebRequest> e. <xref:System.Net.WebClient>

O exemplo consiste em um serviço hospedado internamente e em um cliente executado em um aplicativo de console. À medida que o aplicativo de console é executado, o cliente faz solicitações ao serviço e grava as informações pertinentes das respostas na janela do console.

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Abra a solução para o exemplo de serviço http básico. Ao iniciar o Visual Studio 2012, você deve executar como administrador para que o exemplo seja executado com êxito. Faça isso clicando com o botão direito do mouse no ícone do Visual Studio 2012 e selecionando **Executar como administrador** no menu de contexto.

2. Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione CTRL + F5 para executar o aplicativo de console sem depuração. A janela do console é exibida e fornece o URI do serviço em execução e o URI da página de ajuda HTML para o serviço em execução. Em qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de ajuda em um navegador. À medida que o exemplo é executado, o cliente grava o status da atividade atual.

3. Pressione qualquer tecla para encerrar o exemplo.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
