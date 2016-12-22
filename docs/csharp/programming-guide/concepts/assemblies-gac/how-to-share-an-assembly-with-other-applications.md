---
title: "Como: compartilhar um Assembly com outros aplicativos (c#) | Microsoft Docs"
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
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: compartilhar um Assembly com outros aplicativos (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um conjunto de módulos particular porque eles não se destina a ser usado por outros aplicativos.  
  
 Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [Cache de assemblies global](../Topic/Global%20Assembly%20Cache.md) \(GAC\).  
  
### Compartilhamento de um assembly  
  
1.  Crie o assembly. Para obter mais informações, consulte [Criando assemblies](../Topic/Creating%20Assemblies.md).  
  
2.  Atribua um nome forte ao assembly. Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md).  
  
3.  Atribua informações de versão para o assembly. Para obter mais informações, consulte [Controle de versão de assemblies](../Topic/Assembly%20Versioning.md).  
  
4.  Adicione o assembly no cache de Assembly Global. Para obter mais informações, consulte [Como instalar um assembly no cache de assemblies global](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md).  
  
5.  Acesse os tipos contidos no assembly de outros aplicativos. Para obter mais informações, consulte [Como referenciar um assembly de nome forte](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Programação com assemblies](../Topic/Programming%20with%20Assemblies.md)