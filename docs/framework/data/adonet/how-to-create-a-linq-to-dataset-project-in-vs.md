---
title: Como criar um projeto LINQ to DataSet no Visual Studio
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3add191250a10d1d6016263ada0ba53fc8082717
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Como criar um projeto LINQ to DataSet no Visual Studio
Os diferentes tipos de projetos do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] exigem determinados namespaces importados (Visual Basic) ou diretivas `using` (C#) e referências. O requisito mínimo é uma referência ao System.Core.dll e uma diretiva `using` para <xref:System.Linq>. Por padrão, eles serão fornecidos se você criar um novo projeto [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)]. O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] também exige uma referência para System.Data.dll e System.Data.DataSetExtensions.dll e uma diretiva `Imports` (Visual Basic) ou `using` (C#).  
  
 Se você estiver atualizando um projeto de uma versão anterior do Visual Studio, poderá ter que fornecer manualmente essas referências relacionadas a LINQ. Você também pode ter que definir manualmente o projeto para direcionar a versão 3.5 do .NET Framework.  
  
> [!NOTE]
>  Se você estiver criando a partir de um prompt de comando, você deve referenciar manualmente as DLLs relacionadas a LINQ em `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.  
  
### <a name="to-target-the-net-framework-35"></a>Para direcionar o .NET Framework 3.5  
  
1.  Em [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], crie um novo projeto do Visual Basic ou c#. Como alternativa, você pode abrir um projeto Visual Basic ou c# que foi criado no Visual Studio 2005 e siga os prompts para convertê-lo para um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projeto.  
  
2.  Para um projeto c#, clique o **projeto** menu e clique **propriedades**.  
  
    1.  No **aplicativo** página de propriedades, selecione o .NET Framework 3.5 no **Framework de destino** lista suspensa.  
  
3.  Para um projeto do Visual Basic, clique o **projeto** menu e clique **propriedades**.  
  
    1.  No **compilar** página de propriedades, clique em **opções avançadas de compilação** e, em seguida, selecione o .NET Framework 3.5 no **Framework de destino (todas as configurações)** lista suspensa.  
  
4.  No **projeto** menu, clique em **adicionar referência**, clique no **.NET** guia, role para baixo até **Core**, clique nele e, em seguida, clique em  **Okey**.  
  
5.  Adicione uma diretiva `using` ou um namespace importado para <xref:System.Linq> ao seu arquivo de código-fonte ou projeto.  
  
     Para obter mais informações, consulte [usando diretiva](~/docs/csharp/language-reference/keywords/using-directive.md) ou [como: Adicionar ou remover Namespaces importados (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>Para ativar a funcionalidade LINQ to DataSet  
  
1.  Se necessário, siga as etapas anteriores neste tópico para adicionar uma referência para o System.Core.dll e uma diretiva `using` ou o namespace importado para System.Linq.  
  
2.  Em c# ou Visual Basic, clique no **projeto** menu e clique **adicionar referência**.  
  
3.  No **adicionar referência** caixa de diálogo, clique o **.NET** guia se não estiver na parte superior. Role para baixo até **System. Data** e **System.Data.DataSetExtensions** e clicar neles. Clique o **Okey** botão.  
  
4.  Adicione uma diretiva `using` ou um namespace importado para <xref:System.Data> ao seu arquivo de código-fonte ou projeto. Para obter mais informações, consulte [usando diretiva](~/docs/csharp/language-reference/keywords/using-directive.md) ou [como: Adicionar ou remover Namespaces importados (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
5.  Adicione uma referência ao System.Data.DataSetExtensions.dll para a funcionalidade LINQ to Dataset. Adicione uma referência para System.Data.dll se ainda não existir.  
  
6.  Opcionalmente, adicione uma diretiva `using` ou um namespace importado para `System.Data.Common` ou `System.Data.SqlClient`, dependendo de como você se conecta ao banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [Introdução ao LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
