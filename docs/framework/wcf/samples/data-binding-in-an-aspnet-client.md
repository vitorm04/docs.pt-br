---
title: Associação de dados em um cliente do ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 2db29e0c4cdb87961430b80f317160b90e6756d0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715376"
---
# <a name="data-binding-in-an-aspnet-client"></a>Associação de dados em um cliente do ASP.NET
Este exemplo demonstra como associar dados retornados por um serviço de Windows Communication Foundation típico (WCF) em um aplicativo Web Forms.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta. O exemplo consiste em um cliente Web Forms aplicativo acessível de um navegador e um serviço WCF hospedado pelo Serviços de Informações da Internet (IIS).  
  
 O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido pela interface `IWeatherService`, que expõe uma operação chamada `GetWeatherData`. Esta operação aceita uma matriz de cidades e retorna uma matriz de objetos `WeatherData` que representam a temperatura alta e baixa prevista para uma cidade.  
  
 Na página ASP.NET Client. aspx, um controle Web DataGrid é definido, que contém a representação gráfica dos dados retornados pelo serviço. O código na página. aspx chama o serviço WCF para dados meteorológicos e retorna os dados para uma matriz de objetos `WeatherData`. O DataGrid especifica de onde obter seus dados definindo sua propriedade `DataSource` para essa matriz. A vinculação de dados ocorre com uma chamada para o método `DataBind` do DataGrid. Todo esse código está contido no.`aspx` o método de `Page_Load` da página, portanto, sempre que o usuário atualiza a página do navegador, os dados são atualizados no DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. O cliente deste exemplo é um site da Web que é executado em um servidor Web de desenvolvimento. Para iniciar o servidor Web de desenvolvimento, digite o seguinte no prompt de comando: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Em seguida, navegue até `http://localhost:8000/client`. Para executar esse exemplo entre computadores, substitua todas as referências a `localhost` no arquivo Web. config do cliente pelo nome do computador do servidor.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
