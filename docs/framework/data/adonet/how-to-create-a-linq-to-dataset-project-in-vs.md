---
title: Criar um projeto LINQ to DataSet no Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 91032766248b11e51b90aa788b1c64c140347c25
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802021"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Como criar um projeto LINQ to DataSet no Visual Studio

Os diferentes tipos de projetos LINQ exigem determinadas referências de assembly e namespaces importados (Visual Basic) ou C# [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas (). O requisito mínimo para LINQ é uma referência a *System. Core. dll* e a uma diretiva `using` para <xref:System.Linq>.

Esses requisitos são fornecidos por padrão se você criar um novo C# projeto de aplicativo de console no Visual Studio 2017 ou em uma versão posterior. Se você estiver atualizando um projeto de uma versão anterior do Visual Studio, talvez seja necessário fornecer essas referências relacionadas ao LINQ manualmente.

LINQ to DataSet requer duas referências adicionais a *System. Data. dll* e *System. Data. DataSetExtensions. dll*.

> [!NOTE]
> Se você estiver criando a partir de um prompt de comando, deverá referenciar manualmente as DLLs relacionadas ao LINQ no *%programfiles%\Reference Assemblies\Microsoft\Framework\v3.5*.

## <a name="to-enable-linq-to-dataset-functionality"></a>Para ativar a funcionalidade LINQ to DataSet

Siga estas etapas para habilitar LINQ to DataSet funcionalidade em um projeto existente.

1. Adicione referências a **System. Core**, **System. Data**e **System. Data. DataSetExtensions**.

   Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **referências** e selecione **Adicionar referência**. Na caixa de diálogo **Gerenciador de referências** , selecione **System. Core**, **System. Data**e **System. Data. DataSetExtensions**. Selecione **OK**.

1. Adicione [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas (ou [instruções Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) em Visual Basic) para **System. Data** e **System. Linq**.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. Opcionalmente, adicione uma diretiva de `using` (ou `Imports` instrução) para **System. Data. Common** ou **System. Data. SqlClient**, dependendo de como você se conecta ao banco de dados.

## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ to DataSet](getting-started-linq-to-dataset.md)
