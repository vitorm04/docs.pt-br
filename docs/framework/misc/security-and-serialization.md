---
title: Segurança e serialização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: 634388e3920e0b9dbee85aa3ea555471cee604ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181112"
---
# <a name="security-and-serialization"></a>Segurança e serialização
Como a serialização pode permitir que outro código veja ou modifique dados de ocorrência de objeto <xref:System.Security.Permissions.SecurityPermission> que <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> de outra forma seriam inacessíveis, é necessária uma permissão especial para a serialização de execução de código: com o sinalizador especificado. De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.  
  
 Normalmente, todos os campos de uma instância de objeto são serializados, o que significa que os dados são representados nos dados serializados para a instância. É possível para o código que pode interpretar o formato para determinar quais são os valores dos dados, independente da acessibilidade do membro. Da mesma forma, a desserialização extrai dados da representação serializada e define o estado do objeto diretamente, novamente independentemente das regras de acessibilidade.  
  
 Qualquer objeto que possa conter dados sensíveis à segurança deve ser tornado não serializável, se possível. Se for serializável, tente tornar os campos específicos que não são serializáveis. Se isso não puder ser feito, esteja ciente de que esses dados serão expostos a qualquer código que tenha permissão para serializar e certifique-se de que nenhum código malicioso possa obter essa permissão.  
  
 A <xref:System.Runtime.Serialization.ISerializable> interface destina-se a ser usada apenas pela infra-estrutura de serialização. No entanto, se desprotegido, ele pode potencialmente liberar informações confidenciais. Se você fornecer serialização personalizada implementando **iSerializable**, certifique-se de tomar as seguintes precauções:  
  
- O <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser explicitamente protegido exigindo a **Permissão de Segurança** com a permissão **SerializationFormatter** especificada ou certificando-se de que nenhuma informação sensível seja liberada com a saída do método. Por exemplo:   
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter
    =true)]  
    public override void GetObjectData(SerializationInfo info,
    StreamingContext context)  
    {  
    }  
    ```  
  
- O construtor especial usado para serialização também deve realizar uma validação completa de entrada e deve ser protegido ou privado para ajudar a proteger contra o uso indevido por código malicioso. Ele deve impor as mesmas verificações de segurança e permissões necessárias para obter uma instância de tal classe por qualquer outro meio, como criar explicitamente a classe ou criá-la indiretamente através de algum tipo de fábrica.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
