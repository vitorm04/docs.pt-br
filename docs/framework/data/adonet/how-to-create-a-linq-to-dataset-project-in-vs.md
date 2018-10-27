---
title: Criar um projeto LINQ to DataSet no Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185554"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Como: criar um projeto LINQ to DataSet no Visual Studio

Os diferentes tipos de projetos LINQ exigem determinados namespaces importados (Visual Basic) e referências de assembly ou [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas (c#). O requisito mínimo para LINQ é uma referência a *dll* e uma `using` diretiva <xref:System.Linq>.

Esses requisitos são fornecidos por padrão, se você criar um novo console aplicativo projeto c# no Visual Studio 2017. Se você estiver atualizando um projeto de uma versão anterior do Visual Studio, talvez você precise fornecer essas referências relacionadas a LINQ manualmente.

LINQ to DataSet requer duas referências adicionais ao *dll* e *DataSetExtensions. dll*.

> [!NOTE]
> Se você estiver compilando em um prompt de comando, deverá manualmente referenciar as DLLs relacionadas a LINQ no *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.

## <a name="to-enable-linq-to-dataset-functionality"></a>Para ativar a funcionalidade LINQ to DataSet

Siga estas etapas para habilitar o LINQ para funcionalidade de conjunto de dados em um projeto existente.

1. Adicione referências aos **System. Core**, **System. Data**, e **DataSetExtensions**.

   Na **Gerenciador de soluções**, clique com botão direito no **referências** nó e selecione **Add Reference**. No **Gerenciador de referências** caixa de diálogo, selecione **System. Core**, **System. Data**, e **DataSetExtensions**. Selecione **OK**.

1. Adicione [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas (ou [instruções Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) no Visual Basic) para **System. Data** e **System. LINQ**.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. Opcionalmente, adicione uma `using` diretiva (ou `Imports` instrução) para **Common** ou **System.Data.SqlClient**, dependendo de como você se conecta ao banco de dados.

## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ to DataSet](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
