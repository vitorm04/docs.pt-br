---
title: 'Como: Compartilhar um assembly com outros aplicativos'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972945"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Como: Compartilhar um assembly com outros aplicativos
Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.  

Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC (cache de assembly global)](gac.md).  
  
Para compartilhar um assembly:
  
1. Crie o assembly. Para obter mais informações, consulte [criar assemblies](../../standard/assembly/create.md).  
  
2. Atribua um nome forte ao assembly. Para obter mais informações, confira [Como: assinar um assembly com um nome forte](../../standard/assembly/sign-strong-name.md).  
  
3. Atribua informações de versão ao assembly. Para obter mais informações, consulte [controle de versão do assembly](../../standard/assembly/versioning.md).  
  
4. Adicione seu assembly ao cache de assembly global. Para obter mais informações, confira [Como: Instale um assembly no cache](install-assembly-into-gac.md)de assembly global.  
  
5. Acesse os tipos contidos no assembly de outros aplicativos. Para obter mais informações, confira [Como: Referencie um assembly](../../standard/assembly/reference-strong-named.md)de nome forte.  
  
## <a name="see-also"></a>Consulte também

- [Guia de programação em C#](../../../api/index.md)
- [Conceitos de programação (Visual Basic)](../../../api/index.md)
- [Programa com assemblies](../../standard/assembly/program.md)
