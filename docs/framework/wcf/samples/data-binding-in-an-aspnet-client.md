---
title: Associação de dados em um cliente do ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: dde5ec9ac944b205051b2499c7aceac2e6d84b92
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850227"
---
# <a name="data-binding-in-an-aspnet-client"></a>Associação de dados em um cliente do ASP.NET
Este exemplo demonstra como associar dados retornados por um serviço típico do Windows Communication Foundation (WCF) em um aplicativo de formulários da Web.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta. O exemplo consiste em um aplicativo de formulários da Web acessível a partir de um navegador e um serviço WCF hospedado pelo Internet Information Services (IIS) do cliente.  
  
 O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido o `IWeatherService` interface, que expõe uma operação denominada `GetWeatherData`. Esta operação aceita uma matriz de cidades e retorna uma matriz de `WeatherData` objetos que representam a temperatura alta e baixa prevista para uma cidade.  
  
 Sobre o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] página. aspx de cliente, uma DataGrid Web controle está definido, que contém a representação gráfica dos dados retornados pelo serviço. O código na página. aspx chama o serviço WCF de clima e retorna os dados para uma matriz de `WeatherData` objetos. A grade de dados especifica onde obter seus dados, definindo seu `DataSource` propriedade para essa matriz. A associação de dados ocorre com uma chamada para o DataGrid `DataBind` método. Todo esse código está contido dentro do.`aspx` da página `Page_Load` método, portanto, sempre que o usuário atualiza a página do navegador, os dados é atualizado na DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Cliente de trabalho deste exemplo é um site da Web que é executado em um servidor Web de desenvolvimento. Para iniciar o servidor Web de desenvolvimento, digite o seguinte no prompt de comando: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Em seguida, navegue até `http://localhost:8000/client`. Para executar este exemplo entre computadores, substitua todas as referências a `localhost` no arquivo de Web. config do cliente com o nome do computador do servidor.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
