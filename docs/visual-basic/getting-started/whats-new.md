---
title: Novidades do Visual Basic | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- VB.StartPage.WhatsNew
dev_langs:
- VB
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: 145
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 55cf69a06a047c12f027007ed7180bf74307f2c9
ms.lasthandoff: 03/13/2017

---
# <a name="whats-new-for-visual-basic"></a>Novidades do Visual Basic
Esta página lista os nomes dos principais recursos para cada versão do Visual Basic com descrições dos recursos novos e aprimorados na versão mais recente da linguagem.  
  
## <a name="previous-versions"></a>Versões anteriores  
 Visual Basic / Visual Studio .NET 2002  
 Primeira versão  
  
 Visual Basic / Visual Studio .NET 2003  
 Operadores bit shift, declaração de variável de loop  
  
 Visual Basic / Visual Studio .NET 2005  
Tipo  `My` e tipos auxiliares (acesso ao aplicativo, computador, sistema de arquivos, rede)  
  
 Visual Basic / Visual Studio .NET 2008  
 LINQ (consulta integrada à linguagem), literais XML, inferência de tipos de variável local, inicializadores de objeto, tipos anônimos, métodos de extensão, inferência de tipos `var` local, expressões lambda, operador `if`, métodos parciais, tipos de valor anulável  
  
 Visual Basic, Visual Studio .NET 2010  
 Propriedades autoimplementadas, inicializadores de coleção, continuação de linha implícita, covariância/contravariância genérica, acesso ao namespace global  
  
 Visual Basic / Visual Studio .NET 2012  
 `Async` / `await`, iteradores, atributos de informações  
  
 Visual Basic / Visual Studio .NET 2013  
 Visualizações de tecnologia do .NET Compiler Platform ("Roslyn")  
  
 Visual Basic / Visual Studio .NET 2015  
 Versão atual, consulte abaixo  
  
## <a name="current-version"></a>Versão atual  
 [Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Você pode obter o nome da cadeia de caracteres não qualificada de um tipo ou de um membro para uso em uma mensagem de erro sem realizar hard-coding de uma cadeia de caracteres.  Isso permite que seu código permaneça correto ao refatorar.  Esse recurso também é útil para conectar links MVC do tipo modelo-exibição-controlador e acionar eventos de alteração de propriedade.  
  
 [Interpolação de cadeia de caracteres](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Você pode usar expressões de interpolação de cadeia de caracteres para construir cadeias de caracteres.  Uma expressão de cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém expressões.  Uma cadeia de caracteres interpolada é mais fácil de entender, em relação aos argumentos, do que a [formatação de composição](../../standard/base-types/composite-format.md).  
  
 [Acesso de membro nulo condicional e indexação](../../csharp/language-reference/operators/null-conditional-operators.md)  
 Você pode testar a nulidade de uma maneira sintática muito simples antes de executar uma operação de acesso de membro (`?.`) ou índice (`?[]`).  Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.  Se a referência de objeto ou o operando esquerdo for nulo, as operações retornarão valores nulos.  
  
 [Literais de cadeia de caracteres multilinha](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Literais de cadeia de caracteres podem conter sequências de nova linha.  Você não precisa da solução alternativa antiga de usar `<xml><![CDATA[...text with newlines...]]></xml>.Value`  
  
 Comentários  
 É possível colocar comentários após continuações de linha implícitas, em expressões de inicializador e entre termos de expressão do LINQ.  
  
 Resolução de nome totalmente qualificado mais inteligente  
 Dado um código como `Threading.Thread.Sleep(1000)`, o Visual Basic pesquisava o namespace "Threading", descobria que ele era ambíguo entre System.Threading e System.Windows.Threading e, então, relatava um erro.  Agora, o Visual Basic considera os dois namespaces possíveis juntos.  Se você mostrar a lista de conclusão, o editor do Visual Studio listará membros dos dois tipos na lista de conclusão.  
  
 Literais de data do primeiro ano  
 Você pode ter literais de data no formato aaaa-mm-dd, `#2015-03-17 16:10 PM#`.  
  
 Propriedades de interface readonly  
 Você pode implementar propriedades de interface readonly usando uma propriedade readwrite.  A interface garante a funcionalidade mínima e não impede que uma classe de implementação permita que a propriedade seja definida.  
  
 [TypeOf \<expr> IsNot \<type>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Para facilitar a leitura do seu código, agora você pode usar `TypeOf` com `IsNot`.  
  
 [#Disable Warning \<ID> e #Enable Warning \<ID>](../../visual-basic/language-reference/directives/directives.md)  
 É possível desabilitar e habilitar avisos específicos para regiões dentro de um arquivo de origem.  
  
 Aprimoramentos de comentário de documento XML  
 Ao escrever comentários de documento, você obtém o editor inteligente e suporte de build para validar nomes de parâmetro, tratamento adequado de `crefs` (genéricos, operadores etc.), coloração e refatoração.  
  
 [Definições de interface e módulo parcial](../../visual-basic/language-reference/modifiers/partial.md)  
 Além das classes e structs, você pode declarar interfaces e módulos parciais.  
  
 [Diretivas #Region dentro de corpos de método](../../visual-basic/language-reference/directives/region-directive.md)  
 Você pode colocar delimitadores #Region...#End Region em qualquer lugar em um arquivo, dentro de funções e até mesmo estendê-los por corpos de função.  
  
 [Definições de substituição são sobrecargas implicitamente](../../visual-basic/language-reference/modifiers/overrides.md)  
 Se você adicionar o modificador `Overrides` a uma definição, o compilador adicionará implicitamente `Overloads`, para que você possa digitar menos código em casos comuns.  
  
 CObj permitido em argumentos de atributos  
 O compilador apresentava um erro de que CObj(...) não era uma constante quando usado em construções de atributo.  
  
 Declarando e consumindo métodos ambíguos de interfaces diferentes  
 Anteriormente, o código a seguir gerava erros que impediam você de declarar `IMock` ou chamar `GetDetails` (se eles tivessem sido declarados em C#):  
  
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
  
 Agora, o compilador usará regras de resolução de sobrecarga normais para escolher o `GetDetails` mais apropriado a ser chamado e você pode declarar relações de interface no Visual Basic, como aquelas mostradas no exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [Novidades no Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/ide/whats-new-in-visual-studio)
