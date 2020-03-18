---
title: Enumerações protobuf - gRPC para desenvolvedores WCF
description: Saiba como declarar e usar enumerações em Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148069"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="51e96-103">Enumerações de Protobuf</span><span class="sxs-lookup"><span data-stu-id="51e96-103">Protobuf enumerations</span></span>

<span data-ttu-id="51e96-104">Protobuf suporta tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="51e96-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="51e96-105">Você viu esse suporte na seção anterior, onde um enum foi usado para determinar o tipo de `Oneof` campo.</span><span class="sxs-lookup"><span data-stu-id="51e96-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="51e96-106">Você pode definir seus próprios tipos de enumeração, e o Protobuf irá compilá-los para os tipos c# enum.</span><span class="sxs-lookup"><span data-stu-id="51e96-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span>

<span data-ttu-id="51e96-107">Como você pode usar protobuf com várias línguas, as convenções de nomeação para enumerações são diferentes das convenções C#.</span><span class="sxs-lookup"><span data-stu-id="51e96-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="51e96-108">No entanto, o gerador de código converte os nomes para o caso C# tradicional.</span><span class="sxs-lookup"><span data-stu-id="51e96-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="51e96-109">Se o equivalente pascal-case do nome de campo começa com o nome de enumeração, então ele é removido.</span><span class="sxs-lookup"><span data-stu-id="51e96-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="51e96-110">Por exemplo, na seguinte enumeração protobuf, os `ACCOUNT_STATUS`campos são prefixados com .</span><span class="sxs-lookup"><span data-stu-id="51e96-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="51e96-111">Este prefixo é equivalente ao nome `AccountStatus`de enum pascal-case, .</span><span class="sxs-lookup"><span data-stu-id="51e96-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="51e96-112">O gerador cria um enum C# equivalente ao seguinte código:</span><span class="sxs-lookup"><span data-stu-id="51e96-112">The generator creates a C# enum equivalent to the following code:</span></span>

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

<span data-ttu-id="51e96-113">As definições de enumeração de Protobuf *devem* ter uma constante zero como seu primeiro campo.</span><span class="sxs-lookup"><span data-stu-id="51e96-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="51e96-114">Como em C#, você pode declarar vários campos com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="51e96-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="51e96-115">Mas você deve habilitar explicitamente `allow_alias` essa opção usando a opção no enum:</span><span class="sxs-lookup"><span data-stu-id="51e96-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

<span data-ttu-id="51e96-116">Você pode declarar enumerações no `.proto` nível superior em um arquivo ou aninhados dentro de uma definição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="51e96-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="51e96-117">Enumerações aninhadas — como mensagens aninhadas `.Types` — serão declaradas dentro da classe estática na classe de mensagens geradas.</span><span class="sxs-lookup"><span data-stu-id="51e96-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="51e96-118">Não há como aplicar o atributo [[Bandeiras]](xref:System.FlagsAttribute) a um enum gerado por Protobuf, e protobuf não entende combinações de enum bitwise.</span><span class="sxs-lookup"><span data-stu-id="51e96-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="51e96-119">Veja o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="51e96-119">Look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

<span data-ttu-id="51e96-120">Se você `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`definir para , é serializado como `3`o valor inteiro .</span><span class="sxs-lookup"><span data-stu-id="51e96-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="51e96-121">Quando um cliente ou servidor tenta desserializar o valor, ele não `3`encontrará uma correspondência na definição de enum para .</span><span class="sxs-lookup"><span data-stu-id="51e96-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="51e96-122">O resultado `Region.None`será .</span><span class="sxs-lookup"><span data-stu-id="51e96-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="51e96-123">A melhor maneira de trabalhar com múltiplos valores de `repeated` enum em Protobuf é usar um campo do tipo enum.</span><span class="sxs-lookup"><span data-stu-id="51e96-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="51e96-124">[Próximo](protobuf-any-oneof.md)
>[anterior](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="51e96-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
