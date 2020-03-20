---
title: Associação de dados em um cliente de formulários do Windows
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d538e8a525f8d07e9ac9f57d4b10119907602d90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145040"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Associação de dados em um cliente de formulários do Windows
Esta amostra demonstra como se vincular a dados retornados por um serviço WCF (Windows Communication Foundation) em um aplicativo do Windows Forms.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste artigo.  
  
 Esta amostra demonstra um serviço que implementa um contrato que define um padrão de comunicação solicitação-resposta. A amostra consiste em um aplicativo do Windows Forms (.exe) cliente e um serviço WCF hospedado pelo Internet Information Services (IIS).  
  
 O contrato é `IWeatherService` definido pela interface, que `GetWeatherData`expõe uma operação chamada . Esta operação aceita uma variedade de cidades `WeatherData` e retorna uma matriz de objetos que representam a alta e baixa temperatura prevista para uma cidade.  
  
 A vinculação de dados ocorre no cliente no aplicativo Formulários do Windows. A `DataGridView` é definido no designer Windows Forms, que é uma representação gráfica dos dados. Um intermediário `BindingSource` nomeado também é criado. A fonte `BindingSource` de dados é definida para o conjunto de dados retornado pelo serviço. O objetivo `BindingSource` do é fornecer uma camada de indireção entre os dados e a exibição de dados. Toda a interação com os dados, como navegação, classificação, filtragem `BindingSource` e atualização, é realizada com chamadas para o componente. Para realizar `DataGridView`a vinculação `datasource` de `DataGridView` dados ao `BindingSource` , o do é então definido para o objeto. Todos os dados retornados do serviço WCF são exibidos graficamente para o usuário.  Toda vez que o usuário clica no botão, os dados `DataGridView`retornados são automaticamente atualizados no data-bound .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
