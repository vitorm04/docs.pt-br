---
title: Associação de dados em um cliente do ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c068c1cab5a5b9dad75e781e58076f4066a3b2a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145001"
---
# <a name="data-binding-in-an-aspnet-client"></a>Associação de dados em um cliente do ASP.NET
Esta amostra demonstra como vincular dados retornados por um serviço típico da Windows Communication Foundation (WCF) em um aplicativo web Forms.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra demonstra um serviço que implementa um contrato que define um padrão de comunicação solicitação-resposta. A amostra consiste em um aplicativo Web Forms cliente acessível a partir de um navegador e um serviço WCF hospedado pelo Internet Information Services (IIS).  
  
 O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta. O contrato é `IWeatherService` definido pela interface, que `GetWeatherData`expõe uma operação chamada . Esta operação aceita uma variedade de cidades `WeatherData` e retorna uma matriz de objetos que representam a alta e baixa temperatura prevista para uma cidade.  
  
 Na página ASP.NET cliente .aspx, é definido um controle Web DataGrid, que contém a representação gráfica dos dados retornados pelo serviço. O código na página .aspx chama o serviço WCF para `WeatherData` dados meteorológicos e retorna os dados para uma matriz de objetos. O DataGrid especifica de onde obter seus `DataSource` dados definindo sua propriedade para esse array. A vinculação de dados ocorre com `DataBind` uma chamada para o método do DataGrid. Todo este código está contido dentro do .`aspx` método da `Page_Load` página, então cada vez que o usuário atualiza a página do navegador, os dados são atualizados no DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. O cliente desta amostra é um site da Web que é executado um servidor Web de desenvolvimento. Para iniciar o servidor Web de desenvolvimento, `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`digite o seguinte no prompt de comando: . Em seguida, navegue para `http://localhost:8000/client`. Para executar esta amostra entre computadores, substitua todas as referências no `localhost` arquivo Web.config do cliente pelo nome do computador do servidor.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
