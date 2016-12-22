---
title: "Tipo de dados definido pelo usu&#225;rio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UserDefined"
  - "UDT"
  - "vb.UDT"
  - "User-Defined"
  - "vb.UserDefined"
  - "vb.User-Defined"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], atribuindo"
  - "tipos de dados [Visual Basic], definido pelo usuário"
  - "instrução Structure"
  - "estruturas, como tipos de dados definidos pelo usuário"
  - "tipos [Visual Basic], definido pelo usuário"
  - "tipos de dados definidos pelo usuário"
  - "tipos de dados definidos pelo usuário, declaração de estrutura"
  - "tipos de dados definidos pelo usuário, estruturas em Visual Basic"
  - "tipos de dados definidos pelo usuário, Visual Basic"
  - "tipos definidos pelo usuário"
  - "tipos definidos pelo usuário, declaração de estrutura"
  - "tipos definidos pelo usuário, estruturas em Visual Basic"
  - "tipos definidos pelo usuário, Visual Basic"
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados definido pelo usu&#225;rio
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Mantém os dados em um formato que você define.  O `Structure` a instrução define o formato.  
  
 Suportam a versões anteriores do Visual Basic o tipo definido pelo usuário \(UDT\).  A versão atual expande o UDT para um  *estrutura*.  Uma estrutura é uma concatenação de um ou mais  *membros* de vários tipos de dados.  Visual Basic trata uma estrutura como uma única unidade, embora você também pode acessar seus membros individualmente.  
  
## Comentários  
 Definir e usar um tipo de estrutura de dados, quando você precisa combinar vários tipos de dados em uma única unidade, ou quando nenhum dos tipos de dados elementar atender às suas necessidades.  
  
 O valor padrão de um tipo de estrutura de dados consiste na combinação dos valores padrão de cada um dos seus membros.  
  
## Formato de declaração  
 Uma declaração de estrutura começa com o [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md) e termina com o `End``Structure` instrução.  O `Structure` instrução fornece o nome da estrutura, que também é o identificador do tipo de dados é a definição da estrutura.  Outras partes do código podem usar esse identificador para declarar variáveis, parâmetros e função retornam valores é do tipo de dados dessa estrutura.  
  
 As declarações entre o `Structure` e `End``Structure` instruções definem os membros da estrutura.  
  
## Níveis de acesso de membro  
 Você deve declarar cada membro usando um [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) ou uma instrução que especifica o nível de acesso, como [Público](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), ou [Particular](../../../visual-basic/language-reference/modifiers/private.md).  Se você usar um `Dim` instrução, os padrões de nível de acesso ao público.  
  
## Dicas de Programação  
  
-   **Consumo de Memória.** Assim como com todos os tipos de dado compostos, você não pode calcular, com segurança, o consumo total de memória ao se adicionar as alocações de armazenamento nominais de seus membros.  Além disso, você não pode assumir, com segurança, que a ordem de armazenamento em memória é a mesma das suas declarações.  Se você precisar controlar a disposição de armazenamento de uma estrutura, você pode aplicar o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> à declaração `Structure`.  
  
-   **Considerações de interoperabilidade.** Se você está em uma interface com componentes não escritos para o.NET Framework, para objetos de automação ou COM exemplo, tenha em mente que os tipos definidos pelo usuário em outros ambientes não são compatíveis com os tipos de estrutura de Visual Basic.  
  
-   **Tipos de dados.** Não há nenhuma conversão automática ou para qualquer tipo de estrutura de dados.  Você pode definir os operadores de conversão em sua estrutura usando o [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md), e você pode declarar cada operador de conversão a ser `Widening` ou `Narrowing`.  
  
-   **Caracteres de tipo.** Tipos de dados de estrutura não ter nenhum caractere de tipo literal ou um caractere de tipo de identificador.  
  
-   **Tipos de Framework.** Não há nenhum tipo correspondente na.NET Framework.  Todas as estruturas herdam o.NET Framework "crua" <xref:System.ValueType?displayProperty=fullName>, mas nenhuma estrutura individual corresponde a <xref:System.ValueType?displayProperty=fullName>.  
  
## Exemplo  
 O paradigma a seguir mostra a estrutura da declaração de uma estrutura.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## Consulte também  
 <xref:System.ValueType>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)