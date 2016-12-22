---
title: "Diretiva using (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "usando diretiva [C#]"
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Diretiva using (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A `using` diretiva tem três usos:  
  
-   Para permitir o uso de tipos em um namespace para que você não precisa qualificar o uso de um tipo no namespace:  
  
    ```c#  
    using System.Text;  
    ```  
  
-   Para permitir que você acesse membros estáticos de um tipo sem ter que qualificar o acesso com o nome do tipo:  
  
    ```c#  
    using static System.Math;  
    ```  
  
-   Para criar um alias para um namespace ou um tipo.  Isso é chamado de um *usando diretiva alias*.  
  
    ```c#  
    using Project = PC.MyCompany.Project;  
    ```  
  
 O `using` palavra\-chave também é usado para criar *usando instruções*, ajudar a garantir que <xref:System.IDisposable> objetos como arquivos e as fontes são tratados corretamente.  Consulte [usando a instrução](../../../visual-basic/language-reference/statements/using-statement.md) para obter mais informações.  
  
## Usando o tipo estático  
 Você pode acessar os membros estáticos de um tipo sem ter que qualificar o acesso com o nome do tipo:  
  
```c#  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
  
```  
  
 `Using static` Importa apenas membros estáticos acessíveis e tipos aninhados declarados no tipo especificado.  Membros herdados não serão importados.  Você pode importar de qualquer tipo nomeado com o uso de uma diretiva estática, incluindo os módulos do Visual Basic.  Se aparecem um funções de nível superior F \# nos metadados como membros estáticos de um tipo nomeado cujo nome é um identificador válido do c\#, as funções do F \# podem ser importadas.  
  
 `Using static` faz com que os métodos de extensão declarados no tipo especificado disponível para pesquisa de método de extensão.  No entanto, os nomes dos métodos de extensão não são importados no escopo de referência não qualificada no código.  
  
 Métodos com o mesmo nome importados de diferentes tipos, por diferentes usando diretivas estáticas da mesma forma de namespace ou unidade de compilação de um grupo de método.  Resolução de sobrecarga nesses grupos de método segue as regras normais de c\#.  
  
## Comentários  
 O escopo de um `using` diretiva é limitada para o arquivo no qual ele aparece.  
  
 Criar um `using` alias para facilitar qualificar um identificador para um namespace ou tipo.  O lado direito do uso de um alias diretiva sempre deve ser um tipo totalmente qualificado, independentemente do uso de diretivas que vêm antes dele.  
  
 Criar um `using` diretiva para usar os tipos em um namespace sem ter que especificar o namespace.  A `using` diretiva não dá acesso a quaisquer namespaces aninhados no namespace que você especificar.  
  
 Namespaces vêm em duas categorias: definidos pelo usuário e definidos pelo sistema.  Namespaces definidos pelo usuário são namespaces definidos em seu código.  Para obter uma lista de namespaces definidos pelo sistema, consulte [biblioteca de classes do .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195).  
  
 Para obter exemplos de métodos em outros assemblies de referência, consulte [Criando e usando c\# DLLs](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemplo 1  
  
### Descrição  
 O exemplo a seguir mostra como definir e usar um `using` alias para um namespace:  
  
### Código  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
### Comentários  
 Uso de uma diretiva de alias não pode ter um tipo genérico aberto no lado direito.  Por exemplo, você não pode criar um alias using para uma List \< T \>, mas você pode criar um para obter uma lista \< int \>.  
  
## Exemplo 2  
  
### Descrição  
 O exemplo a seguir mostra como definir um `using` diretiva e uma `using` alias para uma classe:  
  
### Código  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [Namespaces](../../../csharp/programming-guide/namespaces/index.md)   
 [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md)