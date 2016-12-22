---
title: "Como inicializar um dicion&#225;rio com um inicializador de cole&#231;&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "inicializadores de coleção [c#], com dicionário"
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como inicializar um dicion&#225;rio com um inicializador de cole&#231;&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:System.Collections.Generic.Dictionary%602> contém uma coleção de pares chave\/valor.  O método de <xref:System.Collections.Generic.Dictionary%602.Add%2A> leva dois parâmetros, um para a chave e um para o valor.  Para inicializar <xref:System.Collections.Generic.Dictionary%602>, ou qualquer coleção cujo método de `Add` tomar vários parâmetros, incluir cada conjunto de parâmetros em chaves como mostrado no exemplo o seguir.  
  
## Exemplo  
 No exemplo de código, <xref:System.Collections.Generic.Dictionary%602> é inicializado com instâncias do tipo `StudentName`.  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Observe os dois pares de chaves em cada elemento da coleção.  As chaves internos incluem o inicializador de objeto para `StudentName`, e as chaves ultraperiféricas incluem o inicializador para pares chave\/valor que serão adicionados a `students`<xref:System.Collections.Generic.Dictionary%602>.  Finalmente, o inicializador de coleção inteira para o dicionário é incluído em chaves.  
  
## Compilando o código  
 Para executar estes código, copiar e colar a classe em um projeto de aplicativo de console do Visual C\# que foi criado em [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  Por padrão, este projeto utiliza a versão 3,5 de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], e tem uma referência a System.Core.dll e uma diretiva de usar para System.Linq.  Se um ou mais desses requisitos estão faltando no projeto, você pode adicioná\-las manualmente.  Para obter mais informações, consulte [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)