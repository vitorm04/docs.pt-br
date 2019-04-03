---
title: Associação de dados em um cliente de formulários do Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d41310108bfffedc38297f2c981e90007b59fb9a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832145"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Associação de dados em um cliente de formulários do Windows
Este exemplo demonstra como associar aos dados retornados por um serviço do Windows Communication Foundation (WCF) em um aplicativo Windows Forms.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste artigo.  
  
 Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta. O exemplo consiste em um aplicativo de formulários do Windows (.exe) do cliente e um serviço WCF hospedado pelo Internet Information Services (IIS).  
  
 O contrato é definido o `IWeatherService` interface, que expõe uma operação denominada `GetWeatherData`. Esta operação aceita uma matriz de cidades e retorna uma matriz de `WeatherData` objetos que representam a temperatura alta e baixa prevista para uma cidade.  
  
 A associação de dados ocorre no cliente no aplicativo do Windows Forms. Um `DataGridView` é definido no designer de formulários do Windows, que é uma representação gráfica dos dados. Intermediário chamado `BindingSource` também é criado. A fonte de dados de `BindingSource` é definida para a matriz de dados retornada pelo serviço. A finalidade de `BindingSource` é fornecer uma camada de indireção entre os dados e o modo de exibição de dados. Toda a interação com os dados, como navegação, classificação, filtragem e atualização, é realizada com chamadas para o `BindingSource` componente. Para realizar a associação de dados para o `DataGridView`, o `datasource` da `DataGridView` é definido como o `BindingSource` objeto. Todos os dados retornados do serviço WCF, em seguida, é exibido graficamente ao usuário.  Sempre que o usuário clica no botão, os dados retornados são atualizados automaticamente na associação de dados `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
