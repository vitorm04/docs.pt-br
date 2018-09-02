---
title: 'Como: compartilhar um Assembly com outros aplicativos (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: a7f6b49e8389108528c44d7464a2e68149dfa940
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466470"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>Como: compartilhar um Assembly com outros aplicativos (Visual Basic)
Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.  
  
 Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](../../../../framework/app-domains/gac.md) (Cache de Assembly Global).  
  
### <a name="sharing-an-assembly"></a>Compartilhando um assembly  
  
1.  Crie o assembly. Para obter mais informações, consulte [Criando assemblies](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Atribua um nome forte ao assembly. Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Atribua informações de versão ao assembly. Para obter mais informações, consulte [Controle de versão do assembly](../../../../framework/app-domains/assembly-versioning.md).  
  
4.  Adicione o assembly no cache de assembly global. Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Acesse, de outros aplicativos, os tipos contidos no assembly. Para obter mais informações, consulte [Como referenciar um assembly de nome forte](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies e Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Programação com assemblies](../../../../framework/app-domains/programming-with-assemblies.md)
