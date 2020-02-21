---
title: Enumerações Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como declarar e usar enumerações no Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543138"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="2f470-103">Enumerações de Protobuf</span><span class="sxs-lookup"><span data-stu-id="2f470-103">Protobuf enumerations</span></span>

<span data-ttu-id="2f470-104">Protobuf dá suporte a tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="2f470-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="2f470-105">Você viu esse suporte na seção anterior, em que uma enumeração foi usada para determinar o tipo de um campo de `Oneof`.</span><span class="sxs-lookup"><span data-stu-id="2f470-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="2f470-106">Você pode definir seus próprios tipos de enumeração e Protobuf irá compilá-los C# para tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="2f470-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span> 

<span data-ttu-id="2f470-107">Como você pode usar o Protobuf com várias linguagens, as convenções de nomenclatura para enumerações são C# diferentes das convenções.</span><span class="sxs-lookup"><span data-stu-id="2f470-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="2f470-108">No entanto, o gerador de código converte os nomes C# para o caso tradicional.</span><span class="sxs-lookup"><span data-stu-id="2f470-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="2f470-109">Se o equivalente ao caso do Pascal do nome do campo começar com o nome da enumeração, ele será removido.</span><span class="sxs-lookup"><span data-stu-id="2f470-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="2f470-110">Por exemplo, na seguinte Enumeração Protobuf, os campos são prefixados com `ACCOUNT_STATUS`.</span><span class="sxs-lookup"><span data-stu-id="2f470-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="2f470-111">Esse prefixo é equivalente ao nome de enumeração do caso Pascal, `AccountStatus`.</span><span class="sxs-lookup"><span data-stu-id="2f470-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="2f470-112">O gerador cria um C# equivalente de enumeração para o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2f470-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="2f470-113">As definições de enumeração Protobuf *devem* ter uma constante zero como seu primeiro campo.</span><span class="sxs-lookup"><span data-stu-id="2f470-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="2f470-114">Como no C#, você pode declarar vários campos com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="2f470-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="2f470-115">Mas você deve habilitar explicitamente essa opção usando a opção `allow_alias` no enum:</span><span class="sxs-lookup"><span data-stu-id="2f470-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="2f470-116">Você pode declarar enumerações no nível superior em um arquivo de `.proto` ou aninhado em uma definição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2f470-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="2f470-117">Enumerações aninhadas — como mensagens aninhadas — serão declaradas dentro da classe estática `.Types` na classe de mensagem gerada.</span><span class="sxs-lookup"><span data-stu-id="2f470-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="2f470-118">Não há como aplicar o atributo [[flags]](xref:System.FlagsAttribute) a uma enumeração gerada por Protobuf, e o Protobuf não compreende combinações de enums de bits.</span><span class="sxs-lookup"><span data-stu-id="2f470-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="2f470-119">Examine o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f470-119">Look at the following example:</span></span>

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

<span data-ttu-id="2f470-120">Se você definir `product.AvailableIn` como `Region.NorthAmerica | Region.SouthAmerica`, ele será serializado como o valor inteiro `3`.</span><span class="sxs-lookup"><span data-stu-id="2f470-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="2f470-121">Quando um cliente ou servidor tenta desserializar o valor, ele não encontra uma correspondência na definição de enumeração para `3`.</span><span class="sxs-lookup"><span data-stu-id="2f470-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="2f470-122">O resultado será `Region.None`.</span><span class="sxs-lookup"><span data-stu-id="2f470-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="2f470-123">A melhor maneira de trabalhar com vários valores enum em Protobuf é usar um campo `repeated` do tipo enum.</span><span class="sxs-lookup"><span data-stu-id="2f470-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2f470-124">[Anterior](protobuf-any-oneof.md)
>[Próximo](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="2f470-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
