---
title: Associação de dados em um cliente de formulários do Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: a84aeedba89cc7a5c267a0fd1f6c4f604fe80d43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="data-binding-in-a-windows-forms-client"></a>Associação de dados em um cliente de formulários do Windows
Este exemplo demonstra como associar dados retornados por um serviço do Windows Communication Foundation (WCF) em um aplicativo do Windows Forms.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste artigo.  
  
 Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta. O exemplo consiste em um cliente de aplicativo do Windows Forms (.exe) e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço hospedado pelo Internet Information Services (IIS).  
  
 O contrato é definido pelo `IWeatherService` interface, que expõe uma operação denominada `GetWeatherData`. Esta operação aceita uma matriz de cidades e retorna uma matriz de `WeatherData` objetos que representam a temperatura alta e baixa prevista para uma cidade.  
  
 A associação de dados ocorre no cliente no aplicativo Windows Forms. Um `DataGridView` é definido no designer de formulários do Windows, que é uma representação gráfica dos dados. Intermediário chamado `BindingSource` também é criado. A fonte de dados de `BindingSource` é definida para a matriz de dados retornada pelo serviço. A finalidade de `BindingSource` é fornecer uma camada de indireção entre os dados e o modo de exibição de dados. Toda a interação com os dados, como navegar, classificação, filtragem e atualizar, é feita com chamadas para o `BindingSource` componente. Para realizar a associação de dados para o `DataGridView`, o `datasource` do `DataGridView` é definido como o `BindingSource` objeto. Todos os dados retornados do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é exibido graficamente para o usuário.  Toda vez que o usuário clica no botão, os dados retornados são atualizados automaticamente em associada a dados `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Consulte também
