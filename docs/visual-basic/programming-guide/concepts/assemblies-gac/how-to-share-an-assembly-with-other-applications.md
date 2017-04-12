---
title: 'Como: compartilhar um Assembly com outros aplicativos (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8065a66c8f7c7b9ccb9125b060b0c03cde273482
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>Como: compartilhar um Assembly com outros aplicativos (Visual Basic)
Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um conjunto de módulos particular porque eles não se destina a ser usado por outros aplicativos.  
  
 Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC).  
  
### <a name="sharing-an-assembly"></a>Compartilhamento de um assembly  
  
1.  Crie o assembly. Para obter mais informações, consulte [Criando Assemblies](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4).  
  
2.  Atribua um nome forte ao assembly. Para obter mais informações, consulte [como: assinar um Assembly com um nome forte](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
3.  Atribua informações de versão para o assembly. Para obter mais informações, consulte [controle de versão do Assembly](https://msdn.microsoft.com/library/51ket42z).  
  
4.  Adicione o assembly no cache de Assembly Global. Para obter mais informações, consulte [como: instalar um Assembly no Cache de Assembly Global](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743).  
  
5.  Acesse os tipos contidos no assembly de outros aplicativos. Para obter mais informações, consulte [como: referenciar um Assembly de nome forte](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md)
 [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Programação com Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)
