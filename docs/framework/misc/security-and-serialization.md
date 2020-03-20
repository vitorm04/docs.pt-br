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
# <a name="security-and-serialization"></a><span data-ttu-id="4bd31-102">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="4bd31-102">Security and Serialization</span></span>
<span data-ttu-id="4bd31-103">Como a serialização pode permitir que outro código veja ou modifique dados de ocorrência de objeto <xref:System.Security.Permissions.SecurityPermission> que <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> de outra forma seriam inacessíveis, é necessária uma permissão especial para a serialização de execução de código: com o sinalizador especificado.</span><span class="sxs-lookup"><span data-stu-id="4bd31-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="4bd31-104">De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.</span><span class="sxs-lookup"><span data-stu-id="4bd31-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="4bd31-105">Normalmente, todos os campos de uma instância de objeto são serializados, o que significa que os dados são representados nos dados serializados para a instância.</span><span class="sxs-lookup"><span data-stu-id="4bd31-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="4bd31-106">É possível para o código que pode interpretar o formato para determinar quais são os valores dos dados, independente da acessibilidade do membro.</span><span class="sxs-lookup"><span data-stu-id="4bd31-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="4bd31-107">Da mesma forma, a desserialização extrai dados da representação serializada e define o estado do objeto diretamente, novamente independentemente das regras de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="4bd31-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="4bd31-108">Qualquer objeto que possa conter dados sensíveis à segurança deve ser tornado não serializável, se possível.</span><span class="sxs-lookup"><span data-stu-id="4bd31-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="4bd31-109">Se for serializável, tente tornar os campos específicos que não são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="4bd31-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="4bd31-110">Se isso não puder ser feito, esteja ciente de que esses dados serão expostos a qualquer código que tenha permissão para serializar e certifique-se de que nenhum código malicioso possa obter essa permissão.</span><span class="sxs-lookup"><span data-stu-id="4bd31-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="4bd31-111">A <xref:System.Runtime.Serialization.ISerializable> interface destina-se a ser usada apenas pela infra-estrutura de serialização.</span><span class="sxs-lookup"><span data-stu-id="4bd31-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="4bd31-112">No entanto, se desprotegido, ele pode potencialmente liberar informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="4bd31-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="4bd31-113">Se você fornecer serialização personalizada implementando **iSerializable**, certifique-se de tomar as seguintes precauções:</span><span class="sxs-lookup"><span data-stu-id="4bd31-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="4bd31-114">O <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser explicitamente protegido exigindo a **Permissão de Segurança** com a permissão **SerializationFormatter** especificada ou certificando-se de que nenhuma informação sensível seja liberada com a saída do método.</span><span class="sxs-lookup"><span data-stu-id="4bd31-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="4bd31-115">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="4bd31-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="4bd31-116">O construtor especial usado para serialização também deve realizar uma validação completa de entrada e deve ser protegido ou privado para ajudar a proteger contra o uso indevido por código malicioso.</span><span class="sxs-lookup"><span data-stu-id="4bd31-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="4bd31-117">Ele deve impor as mesmas verificações de segurança e permissões necessárias para obter uma instância de tal classe por qualquer outro meio, como criar explicitamente a classe ou criá-la indiretamente através de algum tipo de fábrica.</span><span class="sxs-lookup"><span data-stu-id="4bd31-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd31-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="4bd31-118">See also</span></span>

- [<span data-ttu-id="4bd31-119">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="4bd31-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
