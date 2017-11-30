---
title: "Associação de dados em um cliente de formulários do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 163bd72d9c42680d72c435e8266c75876490a2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a>Associação de dados em um cliente de formulários do Windows
Este exemplo demonstra como associar a dados retornados por uma [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço em um aplicativo do Windows Forms.  
  
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Consulte também
