---
title: "What&#39;s New for Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VB.StartPage.WhatsNew"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "new features, Visual Basic"
  - "what's new [Visual Basic]"
  - "Visual Basic, what's new"
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: 145
caps.handback.revision: 145
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# What&#39;s New for Visual Basic
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Esta página lista os nomes dos recursos principais para cada versão do Visual Basic com descrições dos recursos novos e aprimorados na versão mais recente da linguagem.  
  
## Versões anteriores  
 Visual Studio básico \/Visual .NET 2002  
 Primeira versão  
  
 Visual Studio básico \/Visual .NET 2003  
 Operadores bit shift, a declaração de variável de loop  
  
 Visual Studio básico \/Visual .NET 2005  
 `My` tipos de tipo e auxiliar \(acesso ao aplicativo, computador, sistema de arquivos, rede  
  
 O Visual Studio básico \/Visual .NET 2008  
 LINQ Language Integrated Query \(\), literais XML, a inferência de tipo local, inicializadores, tipos anônimos, métodos de extensão, o local do objeto `var` inferência de tipos, as expressões lambda, `if` operador, métodos parciais, tipos de valor anuláveis  
  
 Visual Basic, Visual Studio 2010 do .NET  
 Propriedades autoimplementadas, inicializadores de coleção, continuação implícita de linha, variância genérica, dinâmico, co\/compensado, acesso de namespace global  
  
 O Visual Studio básico \/Visual .NET 2012  
 `Async` \/ `await`, iteradores, atributos de informações do chamador  
  
 O Visual Studio básico \/Visual .NET 2013  
 visualizações de tecnologia do .NET Compiler Platform \("Roslyn"\)  
  
 O Visual Studio básico \/Visual 2015 .NET  
 Versão atual, consulte abaixo  
  
## Versão atual  
 [Nome](../../csharp/language-reference/keywords/nameof.md)  
 Você pode obter o nome de cadeia de caracteres não qualificado de um tipo ou membro para uso em uma mensagem de erro sem embuti uma cadeia de caracteres.  Isso permite que seu código permaneça correto quando a refatoração.  Esse recurso também é útil para conectar links MVC model\-view\-controller e acionar eventos de propriedade alterada.  
  
 [Interpolação de cadeia de caracteres](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Você pode usar expressões de interpolação de cadeia de caracteres para construir cadeias de caracteres.  Uma expressão de cadeia de caracteres interpolados se parece com uma cadeia de caracteres de modelo que contém expressões.  C\# cria uma cadeia de caracteres, substituindo as expressões com o represenations ToString dos resultados de expressões.  Uma cadeia de caracteres interpolada é mais fácil compreender em relação a argumentos que [Formatação composta](../Topic/Composite%20Formatting.md).  
  
 [Acesso de membro NULL condicional e indexação](../../csharp/language-reference/operators/null-conditional-operators.md)  
 Você pode testar null de maneira muito clara sintática antes de executar um acesso de membro \(`?.`\) ou índice \(`?[]`\) operação.  Esses operadores ajudarão\-lo a escrever menos código para lidar com null verifica, especialmente em ordem decrescente em estruturas de dados.  Se a referência de objeto ou operando esquerda for nula, as operações retorna null.  
  
 [Literais de cadeia de caracteres de várias linhas](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Literais de cadeia de caracteres podem conter seqüências de nova linha.  Você não mais precisa o antigo contornar do uso `<xml><![CDATA[...text with newlines...]]></xml>.Value`  
  
 Comentários  
 Você pode inserir comentários após a continuação implícita de linha, em expressões de inicializador e entre os termos da expressão LINQ.  
  
 Resolução de nome totalmente qualificado mais inteligente  
 Dado o código como `Threading.Thread.Sleep(1000)`, Visual Basic usada para pesquisar o namespace "Threading", descobrir foi ambíguo entre System. Threading e System.Windows.Threading e, em seguida, relatar um erro.  Visual Basic agora considera as duas possíveis namespaces juntos.  Se você exibir a lista de preenchimento, o editor do Visual Studio lista membros de ambos os tipos na lista de conclusão.  
  
 Literais de data do primeiro ano  
 Você pode ter literais de data no formato aaaa\-mm\-dd, `#2015-03-17 16:10 PM#`.  
  
 Propriedades da Interface de somente leitura  
 Você pode implementar propriedades somente leitura da interface usando uma propriedade readwrite.  A interface garante a funcionalidade mínima, e não impede que uma classe de implementação de permitindo à propriedade ser definida.  
  
 [TypeOf \< expr \> IsNot \< tipo \>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Para facilitar a leitura mais do seu código, agora você pode usar `TypeOf` com `IsNot`.  
  
 [Aviso \#Disable \< ID \> e \< ID \> aviso de \#Enable](../../visual-basic/language-reference/directives/directives.md)  
 Você pode desativar e ativar avisos específicos para regiões dentro de um arquivo de origem.  
  
 Aprimoramentos de comentário de documento XML  
 Ao escrever comentários doc, você obtém editor inteligente e criar suporte para validar os nomes de parâmetro adequados de tratamento de `crefs` \(genéricos, operadores, etc.\), colorir e refatoração.  
  
 [Módulo parcial e definições de Interface](../../visual-basic/language-reference/modifiers/partial.md)  
 Além das classes e estruturas, você pode declarar interfaces e módulos parciais.  
  
 [Políticas de \#Region dentro de corpos de método](../../visual-basic/language-reference/directives/region-directive.md)  
 Você pode colocar... \#Region delimitadores \#End região em qualquer lugar em um arquivo, dentro de funções e até mesmo estendê\-los por corpos de função.  
  
 [Definições de substituições são implicitamente sobrecargas](../../visual-basic/language-reference/modifiers/overrides.md)  
 Se você adicionar o `Overrides` modificador a uma definição, o compilador adiciona implicitamente `Overloads` casos, para que você possa digitar menos código em comum.  
  
 CObj permitido em argumentos de atributos  
 O compilador usado para apresentar um erro que CObj\(...\) não era uma constante quando usado em construções de atributo.  
  
 Declarando e consumindo ambíguos métodos de Interfaces diferentes  
 Anteriormente, o código a seguir gerou erros que impediu a declaração `IMock` ou chamar `GetDetails` \(se eles tivessem sido declarados no c\#\):  
  
```vb  
Interface ICustomer  
  Sub GetDetails(x As Integer)  
End Interface  
  
Interface ITime  
  Sub GetDetails(x As String)  
End Interface  
  
Interface IMock : Inherits ICustomer, ITime  
  Overloads Sub GetDetails(x As Char)  
End Interface  
  
Interface IMock2 : Inherits ICustomer, ITime  
End Interface  
  
```  
  
 Agora, o compilador usará as regras de resolução de sobrecarga normal para escolher o mais apropriado `GetDetails` chamar, e você pode declarar relações de interface no Visual Basic, como as mostradas no exemplo.  
  
## Consulte também  
 [O que há de novo no Visual Studio 2015](/visual-studio/ide/what-s-new-in-visual-studio-2015)