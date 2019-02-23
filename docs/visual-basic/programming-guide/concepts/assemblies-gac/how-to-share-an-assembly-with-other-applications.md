---
title: 'Como: Compartilhar um Assembly com outros aplicativos (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 1acd665c702dd3b765cdeffde5470893e7097695
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747684"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>Como: Compartilhar um Assembly com outros aplicativos (Visual Basic)
Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.  
  
 Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](../../../../framework/app-domains/gac.md) (Cache de Assembly Global).  
  
### <a name="sharing-an-assembly"></a>Compartilhando um assembly  
  
1.  Crie o assembly. Para obter mais informações, consulte [Criando assemblies](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Atribua um nome forte ao assembly. Para obter mais informações, confira [Como: Assinar um assembly com um nome forte](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Atribua informações de versão ao assembly. Para obter mais informações, consulte [Controle de versão do assembly](../../../../framework/app-domains/assembly-versioning.md).  
  
4.  Adicione o assembly no cache de assembly global. Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Acesse, de outros aplicativos, os tipos contidos no assembly. Para obter mais informações, confira [Como: Referenciar um assembly de nome forte](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>Consulte também

- [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)
- [Assemblies no .NET](../../../../standard/assembly/index.md)
- [Programação com assemblies](../../../../framework/app-domains/programming-with-assemblies.md)
