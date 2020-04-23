---
title: Como compartilhar um assembly com outros aplicativos
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644285"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Como compartilhar um assembly com outros aplicativos
Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.  

Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC (cache de assembly global)](gac.md).  
  
Para compartilhar um assembly:
  
1. Crie o assembly. Para obter mais informações, consulte [criar assemblies](../../standard/assembly/create.md).  
  
2. Atribua um nome forte ao assembly. Para obter mais informações, consulte [como assinar um assembly com um nome forte](../../standard/assembly/sign-strong-name.md).  
  
3. Atribua informações de versão ao assembly. Para obter mais informações, consulte [controle de versão do assembly](../../standard/assembly/versioning.md).  
  
4. Adicione seu assembly ao cache de assembly global. Para obter mais informações, consulte [como: instalar um assembly no cache de assembly global](install-assembly-into-gac.md).  
  
5. Acesse os tipos contidos no assembly de outros aplicativos. Para obter mais informações, consulte [como referenciar um assembly de nome forte](../../standard/assembly/reference-strong-named.md).  
  
## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../../../api/index.md)
- [Conceitos de programação (Visual Basic)](../../../api/index.md)
- [Programar com assemblies](../../standard/assembly/index.md)
