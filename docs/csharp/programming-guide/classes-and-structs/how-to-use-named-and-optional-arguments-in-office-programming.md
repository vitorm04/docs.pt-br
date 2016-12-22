---
title: "Como usar argumentos nomeados e opcionais na programa&#231;&#227;o do Office (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "argumentos nomeados e opcionais [C#], programação do Office"
  - "argumentos nomeados [C#], programação do Office"
  - "argumentos opcionais [C#], programação do Office"
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: 34
caps.handback.revision: 34
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar argumentos nomeados e opcionais na programa&#231;&#227;o do Office (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Chamados argumentos e argumentos opcionais, introduzidos no [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)], melhorar a legibilidade na programação de C\#, flexibilidade e conveniência. Além disso, esses recursos bastante facilitam o acesso a interfaces COM, como a automação de Microsoft Office de APIs.  
  
 No exemplo a seguir, o método [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) possui dezesseis parâmetros que representam as características de uma tabela, como o número de colunas e linhas, formatação, bordas, fontes e cores.  Todos os parâmetros de dezesseis são opcionais, como na maioria das vezes você não deseja especificar valores específicos para todos eles.  No entanto, sem argumentos nomeados e opcionais, um valor ou um valor de espaço reservado deve ser fornecido para cada parâmetro.  Com argumentos nomeados e opcionais, você pode especificar valores somente para os parâmetros que são necessários para o seu projeto.  
  
 Você deve ter Microsoft Office Word instalado em seu computador para concluir estes procedimentos.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para criar um novo aplicativo de console  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **File**, aponte para **New**, e em seguida, clique em **Project**.  
  
3.  No  **Categorias de modelos de** painel, expanda  **Visual C\#**e, em seguida, clique em  **Windows**.  
  
4.  Procure na parte superior da  **modelos de** o painel para certificar\-se de que  **.NET Framework 4** consta o  **Estrutura de destino** caixa.  
  
5.  No  **modelos de** painel, clique em  **Aplicativo de Console**.  
  
6.  Digite um nome para seu projeto no  **nome** campo.  
  
7.  Clique em **OK**.  
  
     O novo projeto aparece na  **Solution Explorer**.  
  
### Para adicionar uma referência  
  
1.  Em  **Solution Explorer**, o nome do seu projeto com o botão direito e, em seguida, clique em  **Add Reference**.  O  **Add Reference** caixa de diálogo aparece.  
  
2.  Sobre o  **.NET** página, selecione  **Microsoft.Office.Interop.Word** na  **Nome do componente** lista.  
  
3.  Clique em **OK**.  
  
### Para adicionar necessário usando diretivas  
  
1.  Em  **Solution Explorer**, com o botão direito do  **Program. cs** de arquivo e clique em  **Exibir código**.  
  
2.  Adicione o seguinte `using` diretivas para a parte superior do arquivo de código.  
  
     [!CODE [csProgGuideNamedAndOptional#4](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#4)]  
  
### Para exibir texto em um documento do Word  
  
1.  No `Program` da classe em Program. cs, adicione o seguinte método para criar um aplicativo do Word e um documento do Word.  O [Adicionar](http://go.microsoft.com/fwlink/?LinkId=145381) método tem quatro parâmetros opcionais.  Este exemplo usa os valores padrão.  Portanto, sem argumentos são necessários em instrução de chamada.  
  
     [!CODE [csProgGuideNamedAndOptional#6](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#6)]  
  
2.  Adicione o seguinte código no final do método para definir onde exibir texto no documento e o texto a ser exibido.  
  
     [!CODE [csProgGuideNamedAndOptional#7](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#7)]  
  
### Para executar o aplicativo  
  
1.  Adicione a seguinte instrução principal.  
  
     [!CODE [csProgGuideNamedAndOptional#8](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#8)]  
  
2.  Pressione CTRL \+ F5 para executar o projeto.  Um documento do Word é exibida que contém o texto especificado.  
  
### Para alterar o texto a uma tabela  
  
1.  Use o `ConvertToTable` método colocá\-lo em uma tabela.  O método tem dezesseis parâmetros opcionais.  IntelliSense inclui parâmetros opcionais em colchetes, como mostrado na ilustração a seguir.  
  
     ![Lista de parâmetros do método ConvertToTable.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert\_TableParameters")  
Parâmetros de ConvertToTable  
  
     Nomeado e argumentos opcionais permitem que você especifique valores para os parâmetros que você deseja alterar.  Adicione o seguinte código para o final do método `DisplayInWord` para criar uma tabela simples.  O argumento especifica que as vírgulas no texto da seqüência de caracteres na `range` separar as células da tabela.  
  
     [!CODE [csProgGuideNamedAndOptional#9](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#9)]  
  
     Em versões anteriores do C\#, a chamada para `ConvertToTable` requer um argumento de referência para cada parâmetro, conforme mostrado no código a seguir.  
  
     [!CODE [csProgGuideNamedAndOptional#14](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#14)]  
  
2.  Pressione CTRL \+ F5 para executar o projeto.  
  
### Para fazer experiências com outros parâmetros.  
  
1.  Para alterar a tabela para que ele tenha uma coluna e três linhas, substitua a última linha de `DisplayInWord` com a instrução a seguir e em seguida, digite CTRL \+ F5.  
  
     [!CODE [csProgGuideNamedAndOptional#10](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#10)]  
  
2.  Para especificar um formato predefinido para a tabela, substitua a última linha de `DisplayInWord` com a instrução a seguir e em seguida, digite CTRL \+ F5.  O formato pode ser qualquer um do [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) constantes.  
  
     [!CODE [csProgGuideNamedAndOptional#11](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#11)]  
  
## Exemplo  
 O código a seguir inclui o exemplo completo.  
  
 [!CODE [csProgGuideNamedAndOptional#12](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#12)]  
  
## Consulte também  
 [Argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)