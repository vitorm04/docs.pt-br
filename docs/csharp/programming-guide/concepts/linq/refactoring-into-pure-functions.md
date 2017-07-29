---
title: "Refatoração em funções puras (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e3bb704cab77d4ad9895624bf7f721920000378
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="refactoring-into-pure-functions-c"></a>Refatoração em funções puras (C#)
Um aspecto importante de transformações e puras é aprender como o código do refatorar usando funções puras.  
  
> [!NOTE]
>  A nomenclatura comuns em programação funcional é que você refatora programa usando funções puras. No Visual Basic e C++, isso alinha com o uso das funções em linguagens respectivos. No entanto, em C#, as funções são chamadas métodos. Para fins desta discussão, uma função pura é implementada como um método em C#.  
  
 Conforme observado anteriormente nesta seção, uma função pura tem duas características úteis:  
  
-   Não tem efeito colateral. A função não altera quaisquer variáveis ou os dados de qualquer tipo fora da função.  
  
-   É consistente. Dado o mesmo conjunto de dados de entrada, sempre retornará o mesmo valor de saída.  
  
 Uma maneira de fazer a transição para programação funcional é o código existente do refatorar para eliminar efeitos colaterais desnecessários e dependências externas. Dessa maneira, você pode criar versões puras de função do código existente.  
  
 Este tópico descreve o que é uma função pura e o que não é. O tutorial [Tutorial: manipulando conteúdo em um documento WordprocessingML](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) mostra como manipular um documento WordprocessingML e inclui dois exemplos de como refatorar usando uma função pura.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Eliminando efeitos colaterais e dependências externas  
 Os seguintes exemplos contrastam duas funções não puras e uma função pura.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Função não pura que altera um membro de classe  
 No código a seguir, a função de `HypenatedConcat` não é uma função pura, porque altera o membro de dados `aMember` na classe:  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HypenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HypenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 Esse código gera a seguinte saída:  
  
```  
StringOne-StringTwo  
```  
  
 Observe que é irrelevante se os dados modificados têm acesso a `public` ou `private`, ou são um membro de `static` ou um membro de instância. Uma função pura não altera quaisquer dados fora da função.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Função não pura que altera um argumento  
 Além disso, a seguinte versão dessa mesma função não é pura porque modifica o conteúdo do seu parâmetro, `sb`.  
  
```csharp  
public class Program  
{  
    public static void HypenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HypenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 Esta versão do programa gerenciar as mesmas saída que a primeira versão, porque a função de `HypenatedConcat` alterou o valor (estado) do primeiro parâmetro chamar a função de membro de <xref:System.Text.StringBuilder.Append%2A> . Observe que essa mudança ocorre independentemente do fato de que `HypenatedConcat` usa passar o parâmetro de atendimento-por- valor.  
  
> [!IMPORTANT]
>  Para tipos de referência, se você passa um parâmetro por valor, ele resulta em uma cópia de referência a um objeto que está sendo passado. Esta cópia ainda está associada com os mesmos dados de instância que a referência original (até que a variável de referência é atribuído a um novo objeto). a Atendimento-por- referência não necessariamente é necessária para uma função modifique um parâmetro.  
  
### <a name="pure-function"></a>Função pura  
 Seguir essa versão de hows de programa como implementar a função de `HypenatedConcat` como uma função pura.  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 Além disso, esta versão gerencia a mesma linha de saída: `StringOne-StringTwo`. Observe que para manter o valor concatenado, ele é armazenado em `s2`variável intermediária.  
  
 Uma abordagem que pode ser muito útil é escrever as funções que são localmente impuros (isto é, declare e alteram variáveis locais) mas é global pura. Tais funções têm muitas das características desejáveis de composability, mas impedem alguns de linguagem e mais complicados de programação, como ter que usar a recursão quando um loop simples realizaria a mesma coisa.  
  
## <a name="standard-query-operators"></a>Operadores de consulta padrão  
 Uma característica importante dos operadores de consulta padrão é que são implementados como funções puras.  
  
 Para obter mais informações, consulte [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às transformações funcionais puras (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)   
 [Programação funcional versus Programação obrigatória (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

