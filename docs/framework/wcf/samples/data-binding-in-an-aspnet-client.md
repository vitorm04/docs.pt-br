---
title: Associação de dados em um cliente do ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c0f3cbb08f0078bf364ef720635f7afda3257611
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="data-binding-in-an-aspnet-client"></a>Associação de dados em um cliente do ASP.NET
Este exemplo demonstra como associar dados retornados por um serviço típico do Windows Communication Foundation (WCF) em um aplicativo de Web Forms.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta. O exemplo consiste em um aplicativo de Web Forms acessível de um navegador do cliente e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço hospedado pelo Internet Information Services (IIS).  
  
 O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido pelo `IWeatherService` interface, que expõe uma operação denominada `GetWeatherData`. Esta operação aceita uma matriz de cidades e retorna uma matriz de `WeatherData` objetos que representam a temperatura alta e baixa prevista para uma cidade.  
  
 Sobre o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] página. aspx do cliente, uma Web de DataGrid controle é definido, que contém a representação gráfica dos dados retornados pelo serviço. Código de chamadas de página. aspx a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço para os dados de clima e retorna os dados para uma matriz de `WeatherData` objetos. A grade de dados especifica onde obter seus dados, definindo seu `DataSource` propriedade para essa matriz. A associação de dados ocorre com uma chamada para a grade de dados `DataBind` método. Todo esse código está contido dentro do.`aspx` página `Page_Load` método, portanto toda vez que o usuário atualiza a página do navegador, os dados é atualizado em DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Cliente neste exemplo é um site da Web que é executado em um servidor Web de desenvolvimento. Para iniciar o servidor de desenvolvimento da Web, digite o seguinte no prompt de comando: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Em seguida, navegue até http://localhost:8000/client. Para executar esse exemplo em computadores, substitua todas as referências a `localhost` no arquivo Web. config do cliente, com o nome do computador do servidor.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a>Consulte também
