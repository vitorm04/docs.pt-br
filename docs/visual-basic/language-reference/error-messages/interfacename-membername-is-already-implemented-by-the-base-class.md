---
title: "'<interfacename>. <membername>'já foi implementado pela classe base'<baseclassname>'. Reimplementação de <type> assumido"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 64bd7771820c2a4073350b7a5189d3a32c4775be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921323"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>'\<interfacename >. \<membername >' já foi implementado pela classe base\<baseclassname >'. Reimplementação de \<tipo > assumido
Uma propriedade, procedimento ou evento em uma classe derivada usa um `Implements` cláusula especificando um membro de interface que já é implementado na classe base.  
  
 Uma classe derivada pode reimplementar um membro de interface é implementado por sua classe base. Isso não é o mesmo que substituir a implementação de classe base. Para obter mais informações, consulte [implementa](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42015  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você pretende reimplementar o membro de interface, você não precisa realizar nenhuma ação. O código em sua classe derivada acessa o membro reimplementedo, a menos que você use o `MyBase` palavra-chave para acessar a implementação da classe base.  
  
-   Se você não pretende reimplementar o membro de interface, remova o `Implements` cláusula da declaração de propriedade, procedimento ou evento.  
  
## <a name="see-also"></a>Consulte também

- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
