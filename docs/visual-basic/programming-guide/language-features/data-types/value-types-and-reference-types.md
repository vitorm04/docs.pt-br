---
title: "Tipos de valor e refer&#234;ncia | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], tipos de referência"
  - "tipos de dados [Visual Basic], tipos de valor"
  - "tipos de dados de referência"
  - "tipos de referência"
  - "tipos [Visual Basic]"
  - "tipo de dados de valor"
  - "tipos de valor"
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de valor e refer&#234;ncia
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

No Visual Basic, tipos de dados são implementados com base na sua classificação.  Os tipos de dados [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] podem ser classificados de acordo com se uma variável de um determinado tipo armazena seus próprios dados ou um ponteiro para os dados.  Se ela armazena seus próprios dados é um  *tipo de valor* ;se ela tem um ponteiro ao dados em outro lugar da memória é um  *tipo de referência* .  
  
## Tipos de valor  
 Um tipo de dados é um  *tipo de valor*  se ele mantém os dados dentro sua própria alocação de memória.  Tipos de valor incluem o seguinte:  
  
-   Todos os tipos de dados numéricos  
  
-   `Boolean`\[`Char`, e `Date`.  
  
-   Todas as estruturas, mesmo que seus membros são referência tipos  
  
-   Enumerações, pois seu tipo base é sempre `SByte`,`Short`,`Integer`, `Long`, `Byte`, `UShort`,`UInteger`, ou `ULong`  
  
 Cada estrutura é um tipo de valor, mesmo se contiver membros de tipo de referência.  Por esse motivo, o valor tipos como `Char` e `Integer` são implementados por.Estruturas de NET Framework.  
  
 Você pode declarar um tipo de valor usando a palavra reservada, por exemplo, `Decimal`.  Você também pode usar a palavra\-chave `New` para inicializar um tipo de valor.  Isso é especialmente útil se o tipo tem um construtor que aceita parâmetros.  Um exemplo disso é o construtor <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>, que cria um novo valor `Decimal` a partir das partes fornecidas.  
  
## Tipos de referência  
 Um  *tipo de referência*  contém um ponteiro para outro local da memória que mantém os dados.  Tipos de referência incluem o seguinte:  
  
-   `String`  
  
-   Todas as matrizes, mesmo que seus elementos são valor tipos  
  
-   Classe tipos, como <xref:System.Windows.Forms.Form>  
  
-   Delegados  
  
 Uma classe é um  *tipo de referência*.  Por esse motivo, tipos de referência, como `Object` e `String` são suportados pelo [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes.  Observe que cada array é um tipo de referência, mesmo que seus membros são tipos de valor.  
  
 Já que cada tipo de referência representa um subjacente.NET Framework "crua", você deve usar o [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md) palavra\-chave quando você inicializá\-lo.  A instrução a seguir inicializa uma matriz.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## Elementos que são tipos não  
 Os seguintes elementos de programação não se qualificam à medida que digita, porque você não pode especificar qualquer um deles como um tipo de dados de um elemento declarado:  
  
-   Namespaces  
  
-   Módulos  
  
-   Eventos  
  
-   Propriedades e procedimentos  
  
-   Variáveis, constantes e campos  
  
## Trabalhando com o tipo de objeto de dados  
 Você pode atribuir um tipo de referência ou um tipo de valor a uma variável da `Object` tipo de dados.  Uma variável `Object` sempre contém um ponteiro para os dados nunca os dados propriamente ditos.  No entanto, se você atribuir uma tipo de valor uma variável `Object`,ele se comporta como se ele contém os seus próprios dados.  Para obter mais informações, consulte [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Você pode descobrir se um `Object` variável está atuando como um tipo de referência ou um tipo de valor, passando\-os para o <xref:Microsoft.VisualBasic.Information.IsReference%2A> método na <xref:Microsoft.VisualBasic.Information> classe da <xref:Microsoft.VisualBasic?displayProperty=fullName> espaço para nome.  <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>Retorna `True` se o conteúdo da `Object` variável representa um tipo de referência.  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Uso eficiente de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)