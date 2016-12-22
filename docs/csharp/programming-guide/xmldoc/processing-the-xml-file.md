---
title: "Processando o arquivo XML (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "XML [C#], processando"
  - "processamento XML [C#]"
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Processando o arquivo XML (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador gera uma sequência de identificação para cada constructo no seu código que está marcado para gerar a documentação.  \(Para obter informações sobre como marcar seu código, consulte  [Recomendado marcas de comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).\) A sequência de caracteres ID identifica exclusivamente o constructo.  Programas que processam o arquivo XML podem usar a seqüência de caracteres de identificação para identificar o correspondente.Item de metadados\/reflexão do NET Framework que se aplica a documentação.  
  
 O arquivo XML não é uma representação hierárquica de seu código; é uma lista simples que tenha uma identificação gerada para cada elemento.  
  
 O compilador observa as regras a seguir quando ele gera as sequências de identificação:  
  
-   Não há espaço em branco é a seqüência de caracteres.  
  
-   A primeira parte da seqüência de caracteres ID identifica o tipo de membro que está sendo identificado por meio de um único caractere, seguido de dois pontos.  Os seguintes tipos de membro são usados:  
  
    |Caracterer|Descrição|  
    |----------------|---------------|  
    |N|namespace<br /><br /> Não é possível adicionar comentários da documentação a um namespace, mas você pode fazer cref referências a elas, quando houver suporte.|  
    |T|tipo: classe, interface, struct, enum, delegado|  
    |F|campo|  
    |P|propriedade \(incluindo os indexadores ou outras propriedades indexadas\)|  
    |M|método \(incluindo tais métodos especiais como construtores, operadores e assim por diante\)|  
    |E|Evento|  
    |\!|sequência de caracteres de erro<br /><br /> O restante da sequência de caracteres fornece informações sobre o erro.  O compilador C\# gera informações de erro para links que não podem ser resolvidos.|  
  
-   A segunda parte da seqüência de caracteres é o nome totalmente qualificado do item, iniciando na raiz do namespace.  O nome do item, seu tipo \(s\) delimitador e o espaço para nome são separadas por pontos.  Se o nome do item propriamente dito tiver períodos, eles são substituídos pelo hash\-sinal \('\#'\).  Presume\-se que nenhum item tem um sinal de hash diretamente em seu nome.  Por exemplo, o nome totalmente qualificado do construtor String seria "System.String.\#ctor".  
  
-   Para propriedades e métodos, se houver argumentos para o método, a lista de argumentos colocados entre parênteses segue.  Se não houver nenhum argumento, nenhum parêntese estará presente  Os argumentos são separados por vírgulas.  A codificação de cada argumento segue diretamente como ele é codificado em um.Assinatura do NET Framework:  
  
    -   Tipos base.  Tipos de regulares \(ELEMENT\_TYPE\_CLASS ou ELEMENT\_TYPE\_VALUETYPE\) são representados como o nome totalmente qualificado do tipo.  
  
    -   Tipos intrínsecos \(por exemplo, ELEMENT\_TYPE\_I4, ELEMENT\_TYPE\_OBJECT, ELEMENT\_TYPE\_STRING, ELEMENT\_TYPE\_TYPEDBYREF.  e ELEMENT\_TYPE\_VOID\) são representadas como o nome totalmente qualificado do tipo completo correspondente.  Por exemplo, Int32 ou System.TypedReference.  
  
    -   ELEMENT\_TYPE\_PTR é representado como um ' \*' seguindo o tipo modificado.  
  
    -   ELEMENT\_TYPE\_BYREF é representado como uma '@' seguindo o tipo modificado.  
  
    -   ELEMENT\_TYPE\_PINNED é representado como uma ' ^' seguindo o tipo modificado.  O compilador C\# nunca gera isso.  
  
    -   ELEMENT\_TYPE\_CMOD\_REQ é representado como uma ' &#124;' e o nome totalmente qualificado da classe modificador, seguindo o tipo modificado.  O compilador C\# nunca gera isso.  
  
    -   ELEMENT\_TYPE\_CMOD\_OPT é representado como uma '\!' e o nome totalmente qualificado da classe modificador, seguindo o tipo modificado.  
  
    -   ELEMENT\_TYPE\_SZARRAY é representado como "\[\]" seguindo o tipo de elemento da matriz.  
  
    -   ELEMENT\_TYPE\_GENERICARRAY é representado como "?" após o tipo de elemento da matriz.  O compilador C\# nunca gera isso.  
  
    -   ELEMENT\_TYPE\_ARRAY é representado como *lowerbound*:`size`,*lowerbound*:`size` onde o número de vírgulas é o posto \- 1, e os limites inferiores e o tamanho de cada dimensão, se conhecido, são representados no formato decimal.  Se um limite inferior ou o tamanho não for especificado, ele simplesmente é omitido.  Se o limite inferior e o tamanho de uma determinada dimensão forem omitidos, o ':' for omitido, bem.  Por exemplo, uma matriz bidimensional com 1 como os limites inferiores e tamanhos não especificados é \[1:,1:\].  
  
    -   ELEMENT\_TYPE\_FNPTR é representado como "\= FUNC:`type`\(*assinatura*\)", onde `type` é o tipo de retorno, e  *assinatura* é os argumentos do método.  Se não houver nenhum argumento, os parênteses são omitidos.  O compilador C\# nunca gera isso.  
  
     Os seguintes componentes de assinatura não são representados, porque nunca são usadas para diferenciação métodos sobrecarregados:  
  
    -   convenção de chamada  
  
    -   tipo de retorno  
  
    -   ELEMENT\_TYPE\_SENTINEL  
  
-   Para conversão operadores somente \(op\_Implicit e op\_Explicit\), o valor de retorno do método é codificado como um ' ~' seguido do tipo de retorno, como codificado acima.  
  
-   Para tipos genéricos, o nome do tipo será ser seguido por uma escala de back e, em seguida, um número que indica o número de parâmetros de tipo genérico.  Por exemplo,  
  
     `<member name="T:SampleClass`2">`é a marca para um tipo que é definido como `public class SampleClass\<T, U>`.  
  
     Para tirar os tipos genéricos como parâmetros de métodos, os parâmetros de tipo genérico são especificados como números precedidos de tiques traseiro \(por exemplo, ' 0,'1\).  Cada número que representa uma notação de matriz baseada em zero para os parâmetros genéricos do tipo.  
  
## Exemplos  
 Os seguintes exemplos mostram como a identificação de seqüências de caracteres para uma classe e seus membros seriam gerados:  
  
 [!CODE [csProgGuidePointers#21](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#21)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Comentários de documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)