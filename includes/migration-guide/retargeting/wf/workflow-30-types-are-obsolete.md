---
ms.openlocfilehash: 70acbb571921c5f72ecaa26b26136a77532ad220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234598"
---
### <a name="workflow-30-types-are-obsolete"></a>Os tipos do WorkFlow 3.0 estão obsoletos

|   |   |
|---|---|
|Detalhes|As APIs (aquelas do namespace System.Workflow) do WWF (Windows Workflow Foundation) 3.0 agora estão obsoletas.|
|Sugestão|Agora devem ser usadas as novas APIs (em System.Activities) do WWF 4.0. Um exemplo de como usar as novas APIs pode ser encontrado [aqui](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), e outras diretrizes estão disponíveis [aqui](https://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx). Como alternativa, uma vez que as APIs do WWF 3.0 ainda têm suporte, elas poderão ser usadas, e o aviso de hora da compilação deve ser evitado suprimindo-o ou usando um compilador mais antigo.|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Redirecionando|
