---
title: Espera para atividades de entrada
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b9e7942ced071a795f1bf408ca4778a216cd85e4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="wait-for-input-activity"></a>Espera para atividades de entrada
Este exemplo demonstra como criar indicadores nomeados em um fluxo de trabalho. Windows Workflow Foundation (WF) não fornece uma atividade para a criação de indicador declarativa. Portanto, quando você deseja criar um indexador no fluxo de trabalho, você deve escrever uma atividade personalizado que o criar. A atividade de `WaitForInput` definida neste exemplo fornece essa funcionalidade, de modo que os usuários podem criar indicadores declarativamente dentro de um fluxo de trabalho.  
  
## <a name="projects-in-this-sample"></a>Projetos nisso exemplo  
  
|**Nome do projeto**|**Descrição**|**Arquivos principais**|  
|-|-|-|  
|WaitForInput|Contém a atividade de `WaitForInput` e o designer|WaitForInput.cs<br /><br /> definição de atividade de`WaitForInput` .|  
|||WaitForInputDesigner.xaml<br /><br /> Designer personalizado para atividades de `WaitForInput` .|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> Conversor de tipos WPF usado para atualizar o tipo genérico de atividade no designer.|  
|WaitForInputTestClient|Exemplo do aplicativo cliente que configura e executa um fluxo de trabalho usando várias atividades de WaitForInput utilizando o designer de fluxo de trabalho.|Sequence1.xaml<br /><br /> Um fluxo de trabalho sequencial que usa a atividade de `WaitForInput` .|  
|||Module.vb<br /><br /> Executa uma instância de fluxo de trabalho definido em Sequence1.xaml.|  
  
## <a name="waitforinput-activity"></a>Atividade de WaitForInput  
 A atividade de `WaitForInput` cria um indexador chamado em um fluxo de trabalho. O indexador espera um sinal e receber dados do seu tipo configurado. Depois que o indexador é que os dados passados no fluxo de trabalho estão disponíveis através da propriedade de `Result` .  
  
 A atividade de `WaitForInput` deriva da classe de <xref:System.Activities.NativeActivity> porque ele deve criar os indicadores, que são acessíveis somente por meio da classe <xref:System.Activities.NativeActivityContext> .  
  
 A atividade tem três atributos aplicados a ele associando um designer, adicionando recurso genérica do argumento que pode ser atualizado, e definindo o tipo genérico padrão para um. A atividade também tem os argumentos listados na tabela a seguir.  
  
|**Nome**|**Tipo**|**Descrição**|  
|-|-|-|  
|TResult|Argumento genérico (TResult)|Tipo do indexador. Este é o tipo de dados a serem passados para o marcador quando continuado.|  
|BookmarkName|InArgument\<cadeia de caracteres >|Nome do indexador.|  
|Resultado|InArgument\<TResult >|Os dados passados à atividade quando o indexador é continuado.|  
  
## <a name="waitforinput-activity-designer"></a>Designer de atividade de WaitForInput  
 O designer de atividade de `WaitForInput` é implementado no arquivo de WaitForInputDesigner.xaml. A atividade de `WaitForInput` e o designer são incluídos no mesmo assembly. O gráfico a seguir mostra a atividade de `WaitForInput` na caixa de ferramentas em uma categoria que tem o mesmo nome que o assembly.  
  
 ![Captura de tela da caixa de ferramentas WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 O gráfico a seguir mostra o designer de `WaitForInput` . Porque, a atividade de `WaitForInput` é muito básica, o designer permite definir os argumentos diretamente na superfície de designer.  
  
 ![Designer de atividade WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de WaitForInput.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para iniciar o exemplo sem depuração, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`