---
title: Associação de dados em um cliente de formulários do Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: c91f413cd5ef41fcbe85c083f2bcfb77a3c957a5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039876"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Associação de dados em um cliente de formulários do Windows
Este exemplo demonstra como associar dados retornados por um serviço Windows Communication Foundation (WCF) em um aplicativo Windows Forms.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste artigo.  
  
 Este exemplo demonstra um serviço que implementa um contrato que define um padrão de comunicação de solicitação-resposta. O exemplo consiste em um cliente Windows Forms aplicativo (. exe) e um serviço WCF hospedado pelo Serviços de Informações da Internet (IIS).  
  
 O contrato é definido pela `IWeatherService` interface, que expõe uma operação chamada. `GetWeatherData` Esta operação aceita uma matriz de cidades e retorna uma matriz de `WeatherData` objetos que representam a temperatura alta e baixa prevista para uma cidade.  
  
 A vinculação de dados ocorre no cliente no aplicativo Windows Forms. Um `DataGridView` é definido no designer de Windows Forms, que é uma representação gráfica dos dados. Um intermediário chamado `BindingSource` também é criado. A fonte de dados `BindingSource` de é definida como a matriz de dados retornada pelo serviço. A finalidade do `BindingSource` é fornecer uma camada de indireção entre os dados e a exibição de dados. Toda a interação com os dados, como navegação, classificação, filtragem e atualização, é realizada com chamadas para o `BindingSource` componente. Para realizar a vinculação de dados `DataGridView`ao, `datasource` o de `DataGridView` é definido para o `BindingSource` objeto. Todos os dados retornados do serviço WCF são exibidos graficamente para o usuário.  Toda vez que o usuário clica no botão, os dados retornados são atualizados automaticamente na associação `DataGridView`de dados.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
