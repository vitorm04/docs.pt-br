---
title: Como compartilhar um assembly com outros aplicativos (C#) | Microsoft Docs
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
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 79397b18b67becf91d04358ea62cb2351be7d252
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Como compartilhar um assembly com outros aplicativos (C#)
Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.  
  
 Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (Cache de Assembly Global).  
  
### <a name="sharing-an-assembly"></a>Compartilhando um assembly  
  
1.  Crie o assembly. Para obter mais informações, consulte [Criando assemblies](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4).  
  
2.  Atribua um nome forte ao assembly. Para obter mais informações, consulte [Como assinar um assembly com um nome forte](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
3.  Atribua informações de versão ao assembly. Para obter mais informações, consulte [Controle de versão do assembly](https://msdn.microsoft.com/library/51ket42z).  
  
4.  Adicione o assembly no cache de assembly global. Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743).  
  
5.  Acesse, de outros aplicativos, os tipos contidos no assembly. Para obter mais informações, consulte [Como referenciar um assembly de nome forte](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)   
 [Programação com assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)
