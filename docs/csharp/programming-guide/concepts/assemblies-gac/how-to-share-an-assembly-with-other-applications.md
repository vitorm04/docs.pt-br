---
title: 'Como: Compartilhar um assembly com outros aplicativos (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314783"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Como: Compartilhar um assembly com outros aplicativos (C#)
Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.  
  
 Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](../../../../framework/app-domains/gac.md) (Cache de Assembly Global).  
  
### <a name="sharing-an-assembly"></a>Compartilhando um assembly  
  
1. Crie o assembly. Para obter mais informações, consulte [Criando assemblies](../../../../framework/app-domains/create-assemblies.md).  
  
2. Atribua um nome forte ao assembly. Para obter mais informações, confira [Como: Assinar um assembly com um nome forte](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3. Atribua informações de versão ao assembly. Para obter mais informações, consulte [Controle de versão do assembly](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4. Adicione o assembly no cache de assembly global. Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5. Acesse, de outros aplicativos, os tipos contidos no assembly. Para obter mais informações, confira [Como: Referenciar um assembly de nome forte](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)
- [Programação com assemblies](../../../../framework/app-domains/programming-with-assemblies.md)
