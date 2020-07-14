---
title: Segurança e serialização
description: Leia sobre segurança e serialização. Use SecurityPermission com o sinalizador SerializationFormatter especificado para ver ou modificar dados de instância de objeto.
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
ms.openlocfilehash: 79952ceee4c8b771aaadd4fc97a547bc65136770
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281258"
---
# <a name="security-and-serialization"></a><span data-ttu-id="8bd7b-104">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="8bd7b-104">Security and Serialization</span></span>
<span data-ttu-id="8bd7b-105">Como a serialização pode permitir que outro código veja ou modifique dados de instância de objeto que, de outra forma, seriam inacessíveis, uma permissão especial é necessária para o código que executa a serialização: <xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> sinalizador especificado.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-105">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="8bd7b-106">De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-106">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="8bd7b-107">Normalmente, todos os campos de uma instância de objeto são serializados, o que significa que os dados são representados nos dados serializados da instância.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-107">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="8bd7b-108">É possível que o código possa interpretar o formato para determinar quais são os valores de dados, independentemente da acessibilidade do membro.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-108">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="8bd7b-109">Da mesma forma, a desserialização extrai dados da representação serializada e define o estado do objeto diretamente, independentemente das regras de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-109">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="8bd7b-110">Qualquer objeto que possa conter dados sensíveis à segurança deve se tornar não serializável, se possível.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-110">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="8bd7b-111">Se ele precisar ser serializável, tente criar campos específicos que contenham dados confidenciais não serializáveis.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-111">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="8bd7b-112">Se isso não puder ser feito, lembre-se de que esses dados serão expostos a qualquer código que tenha permissão para serializar e certifique-se de que nenhum código mal-intencionado possa obter essa permissão.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-112">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="8bd7b-113">A <xref:System.Runtime.Serialization.ISerializable> interface destina-se ao uso somente pela infraestrutura de serialização.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-113">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="8bd7b-114">No entanto, se desprotegido, ele poderá liberar informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-114">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="8bd7b-115">Se você fornecer serialização personalizada implementando **ISerializable**, certifique-se de tomar as seguintes precauções:</span><span class="sxs-lookup"><span data-stu-id="8bd7b-115">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="8bd7b-116">O <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser explicitamente protegido, exigindo a permissão **SecurityPermission** com **SerializationFormatter** especificada ou garantindo que nenhuma informação confidencial seja lançada com a saída do método.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-116">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="8bd7b-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8bd7b-117">For example:</span></span>  
  
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
  
- <span data-ttu-id="8bd7b-118">O Construtor especial usado para serialização também deve executar uma validação de entrada completa e deve ser protegido ou privado para ajudar a proteger contra uso indevido de código mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-118">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="8bd7b-119">Ele deve impor as mesmas verificações de segurança e as permissões necessárias para obter uma instância de tal classe por outros meios, como criar explicitamente a classe ou criá-la indiretamente por meio de algum tipo de fábrica.</span><span class="sxs-lookup"><span data-stu-id="8bd7b-119">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd7b-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="8bd7b-120">See also</span></span>

- [<span data-ttu-id="8bd7b-121">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="8bd7b-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
