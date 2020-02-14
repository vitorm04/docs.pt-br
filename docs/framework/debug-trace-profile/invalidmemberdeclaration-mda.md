---
title: MDA invalidMemberDeclaration
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216293"
---
# <a name="invalidmemberdeclaration-mda"></a>MDA invalidMemberDeclaration
O MDA (Assistente de Depuração Gerenciado) de `invalidMemberDeclaration` é ativado para relatar um erro que ocorre ao determinar como realizar marshaling dos parâmetros de um membro a ser chamado do COM.  
  
## <a name="symptoms"></a>Sintomas  
 Uma falha de HRESULT é retornada ao COM sem o método gerenciado ter sido chamado.  
  
## <a name="cause"></a>Causa  
 Isso ocorre provavelmente devido a um atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> incompatível em um dos parâmetros.  
  
## <a name="resolution"></a>Resolução  
 Especifique atributos <xref:System.Runtime.InteropServices.MarshalAsAttribute> válidos nos parâmetros.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o runtime  
 Esse MDA não tem efeito sobre o CLR.  
  
## <a name="output"></a>Saída  
 Uma mensagem informativa contendo o nome do membro, o nome do tipo e a mensagem de erro.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../interop/interop-marshaling.md)
