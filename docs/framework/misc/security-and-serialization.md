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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4deadc175bd4cc3635a6c8d8d8b80100b5a9938
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868830"
---
# <a name="security-and-serialization"></a>Segurança e serialização
Como a serialização pode permitir que outro código veja ou modifique os dados da instância de objeto de outro modo seria inacessíveis, uma permissão especial é necessária de código para executar a serialização: <xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> sinalizador especificado. De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.  
  
 Normalmente, todos os campos de uma instância de objeto são serializados, que significa que os dados são representados nos dados serializados para a instância. É possível para o código que pode interpretar o formato para determinar quais os valores de dados, independentemente da acessibilidade do membro. Da mesma forma, a desserialização extrai dados da representação serializada e define o estado de objeto diretamente, novamente, independentemente de regras de acessibilidade.  
  
 Qualquer objeto que pode conter dados confidenciais de segurança deve ser feito não serializáveis, se possível. Se ele deve ser serializável, tente fazer a campos específicos que contêm dados confidenciais não serializável. Se isso não pode ser feito, lembre-se de que esses dados serão expostos em qualquer código que tem permissão para serializar e certifique-se de que nenhum código mal-intencionado pode obter essa permissão.  
  
 O <xref:System.Runtime.Serialization.ISerializable> interface destina para uso apenas pela infraestrutura de serialização. No entanto, se desprotegido, ele pode liberar potencialmente informações confidenciais. Se você fornecer serialização personalizada implementando **ISerializable**, certifique-se de tomar as seguintes precauções:  
  
-   O <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser explicitamente protegido por mais exigentes de **SecurityPermission** com **SerializationFormatter** permissão especificada ou pela certificando-se de que nenhum minúsculas informações são liberadas com a saída do método. Por exemplo:  
  
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
  
-   O construtor especial usado para serialização também deve executar a validação completa de entrada e deve ser protegida ou privada para ajudar a proteger contra uso indevido pelo código mal-intencionado. Ele deve aplicar o mesmo verificações de segurança e as permissões necessárias para obter uma instância dessa classe por outros meios, como criar explicitamente a classe ou indiretamente criá-lo por meio de algum tipo de fábrica.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
