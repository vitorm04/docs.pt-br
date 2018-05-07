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
ms.openlocfilehash: a30e80b1b4a412405787c0c14ad58995a2d7fffc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-serialization"></a>Segurança e serialização
Como a serialização pode permitir que outro código ver ou modificar dados de instância de objeto que possa ser acessados, uma permissão especial é necessária de código para executar a serialização: <xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> sinalizador especificado. De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.  
  
 Normalmente, todos os campos de uma instância do objeto são serializados, que significa que os dados são representados nos dados serializados para a instância. É possível para o código que pode interpretar o formato para determinar quais os valores de dados, independentemente de acessibilidade do membro. Da mesma forma, desserialização extrai dados da representação serializada e define o estado do objeto diretamente, novamente independentemente de regras de acessibilidade.  
  
 Qualquer objeto que pode conter dados confidenciais deve ser feito nonserializable, se possível. Se ele deve ser serializável, tente fazer campos específicos que contêm dados confidenciais serializável. Se isso não pode ser feito, lembre-se de que esses dados serão expostos a qualquer código que tem permissão para serializar e certifique-se de que nenhum código mal-intencionado pode obter essa permissão.  
  
 O <xref:System.Runtime.Serialization.ISerializable> interface é destinada ao uso somente pela infraestrutura de serialização. No entanto, se desprotegidos, ele pode liberar potencialmente informações confidenciais. Se você fornecer a serialização personalizada implementando **ISerializable**, certifique-se de tomar as seguintes precauções:  
  
-   O <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser explicitamente protegido por mais exigentes o **SecurityPermission** com **comoSerializationFormatter** permissão especificado ou por certificando-se de que não diferencia informações são liberadas com a saída do método. Por exemplo:  
  
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
  
-   O construtor especial usado para serialização também deve executar a validação da entrada completa e deve ser protegida ou privada para ajudar a proteger contra o uso indevido por códigos mal-intencionados. Ele deve aplicar o mesmo verificações de segurança e permissões necessárias para obter uma instância dessa classe por outros meios, como criar explicitamente a classe ou indiretamente criá-lo por meio de algum tipo de fábrica.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
