---
title: "Aplicabilidade da transformação funcional (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7196e128a6d61b2b28e955a79561db2b9a5e51b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="applicability-of-functional-transformation-c"></a>Aplicabilidade da transformação funcional (C#)
Transformações e puras são aplicáveis em uma variedade de situações.  
  
 A abordagem funcional de transformação é mais idealmente consultando e manipulando dados; estruturados portanto couber bem com as tecnologias LINQ. No entanto, a transformação funcional tem uma aplicabilidade muito maior do que o uso com LINQ. Alguns processam onde o foco principal está em transformar dados de um formulário para outro provavelmente deve ser considerado como um candidato para a transformação funcional.  
  
 Essa abordagem é aplicável a muitos problemas que não podem parecer à primeira vista para ser um candidato. Usado em conjunto ou separadamente com LINQ, a transformação funcional deve ser considerada para as seguintes áreas:  
  
-   Documentos com base em XML. Os dados bem formado do dialeto de XML podem facilmente ser manipulados pela transformação funcional. Para obter mais informações, consulte [Transformação funcional de XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Outros formatos de arquivo estruturados. De Windows.ini arquivos aos documentos de texto sem formatação, a maioria dos arquivos têm qualquer estrutura que se empresta a análise e a transformação.  
  
-   Os protocolos de streaming de dados. Os dados de codificação e nos dados de decodificação dos protocolos de comunicação geralmente podem ser representados por um funcional simples tornam-se.  
  
-   Dados de RDBMS e de OODBMS. Os bases de dados relacionais e orientados a objeto, assim como XML, são estruturados fontes de dados amplamente usadas.  
  
-   Matemático, estatística, e soluções de ciência. Esses campos tendem a manipular grandes conjuntos de dados para ajudar o usuário em visualizar, em estimar, ou realmente em resolver problemas não triviais.  
  
 Como descrito em [Refatoração em funções puras(C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), usar funções puras é um exemplo de programação funcional. Em adicional a seus benefícios imediatos, usar funções puras fornece a experiência valiosa no pensamento sobre problemas de uma perspectiva funcional de transformação. Essa abordagem pode também ter o impacto principal no design do programa e da classe. Isso é especialmente verdadeiro quando um problema se empresta a uma solução de transformação de dados como descrito acima.  
  
 Embora eles sejam além do escopo deste tutorial, os projetos que são influenciados pela perspectiva funcional de transformação tendem a centralizar sobre processam mais do que em objetos como atores, e a solução resultante tendem a ser implementados como série de transformações em grande escala, em vez de alterações de estado individuais de objeto.  
  
 Além disso, lembre-se que o C# dá suporte as abordagens imperativa e funcional, portanto, o melhor design para o seu aplicativo poderá incorporar os elementos de ambos.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às transformações funcionais puras (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Transformação funcional XML (c#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
 [Refatoração em funções puras (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
