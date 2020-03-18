---
title: Serialização binária
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 9df9b73a1a1347b952d76b76c9058578f5e9f401
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400634"
---
# <a name="binary-serialization"></a><span data-ttu-id="88a6c-102">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="88a6c-102">Binary serialization</span></span>

<span data-ttu-id="88a6c-103">A serialização pode ser definida como o processo de armazenar o estado de um objeto em uma mídia de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="88a6c-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="88a6c-104">Durante esse processo, os campos públicos e privados do objeto e o nome da classe, incluindo o assembly que contém a classe, são convertidos em um fluxo de bytes, que é em seguida escrito em um fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="88a6c-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="88a6c-105">Quando o objeto é desserializado posteriormente, um clone exato do objeto original é criado.</span><span class="sxs-lookup"><span data-stu-id="88a6c-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="88a6c-106">Ao implementar um mecanismo de serialização em um ambiente orientado a objeto, você precisará fazer algumas trocas entre a facilidade de uso e a flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="88a6c-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="88a6c-107">O processo pode ser automatizado em grande parte, contanto que você tenha controle suficiente sobre o processo.</span><span class="sxs-lookup"><span data-stu-id="88a6c-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="88a6c-108">Por exemplo, em algumas situações, a serialização binária simples pode não ser suficiente, ou pode haver um motivo específico para decidir quais campos em uma classe precisam ser serializados.</span><span class="sxs-lookup"><span data-stu-id="88a6c-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="88a6c-109">As seções a seguir examinam o mecanismo de serialização robusto fornecido com o .NET e destacam vários recursos importantes que permitem personalizar o processo para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="88a6c-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="88a6c-110">O estado de um objeto codificado UTF-8 ou UTF-7 não é preservado se o objeto é serializado e desserializado usando versões diferentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88a6c-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="88a6c-111">A serialização binária permite modificar membros privados dentro de um objeto e, portanto, alterar o estado dele.</span><span class="sxs-lookup"><span data-stu-id="88a6c-111">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="88a6c-112">Por causa disso, outros frameworks <xref:System.Text.Json?displayProperty=fullName>de serialização, como , que operam na superfície pública da API são recomendados.</span><span class="sxs-lookup"><span data-stu-id="88a6c-112">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="88a6c-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="88a6c-113">.NET Core</span></span>

<span data-ttu-id="88a6c-114">.NET Core suporta serialização binária para um subconjunto de tipos.</span><span class="sxs-lookup"><span data-stu-id="88a6c-114">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="88a6c-115">Você pode ver a lista de tipos suportados na seção [Tipos Serializáveis](#serializable-types) a seguir.</span><span class="sxs-lookup"><span data-stu-id="88a6c-115">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="88a6c-116">Os tipos listados são garantidos para serem serializáveis entre as versões .NET Framework 4.5.1 e posteriores e entre as versões .NET Core 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="88a6c-116">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="88a6c-117">Outras implementações .NET, como a Mono, não são suportadas oficialmente, mas também devem funcionar.</span><span class="sxs-lookup"><span data-stu-id="88a6c-117">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="88a6c-118">Tipos serializáveis</span><span class="sxs-lookup"><span data-stu-id="88a6c-118">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="88a6c-119">Type</span><span class="sxs-lookup"><span data-stu-id="88a6c-119">Type</span></span> | <span data-ttu-id="88a6c-120">Observações</span><span class="sxs-lookup"><span data-stu-id="88a6c-120">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-121">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-121">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-122">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-122">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-123">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-124">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-125">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-126">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-127">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-128">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-129">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-130">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-131">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-132">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-133">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-134">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="88a6c-135">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-136">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-137">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-138">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-139">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-140">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-140">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="88a6c-141">A serialização do .NET Framework para o .NET Core não é suportada.</span><span class="sxs-lookup"><span data-stu-id="88a6c-141">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-142">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-142">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="88a6c-143">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-143">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-144">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-145">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-146">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-147">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-148">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-149">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-150">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="88a6c-151">Começando em .NET Core 2.0.2 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="88a6c-151">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-152">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-153">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-153">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-154">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-155">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="88a6c-156">Se você `RemotingFormat` `SerializationFormat.Binary`definir, ele só pode ser trocado com as versões .NET Core 2.1 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="88a6c-156">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-157">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-158">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-158">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-159">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-160">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-161">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-162">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-163">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-164">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-165">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-166">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-167">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-168">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-169">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-169">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="88a6c-170">A serialização do .NET Framework para o .NET Core não é suportada</span><span class="sxs-lookup"><span data-stu-id="88a6c-170">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-171">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-171">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-172">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-172">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-173">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-174">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-175">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-176">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-177">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-178">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-179">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="88a6c-180">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-181">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-182">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-183">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-184">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-185">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-186">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-187">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-188">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-189">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-190">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-191">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-192">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-193">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-194">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-195">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-196">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-197">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-198">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-199">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-200">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-201">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-202">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-203">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-204">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-205">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="88a6c-206">A partir de .NET Core 2.0.6.</span><span class="sxs-lookup"><span data-stu-id="88a6c-206">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-207">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-208">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-208">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-209">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-210">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="88a6c-211">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-212">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-213">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-214">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-215">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-216">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-217">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-218">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-219">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-220">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-221">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-222">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-223">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-224">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-225">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-226">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-227">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-228">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-229">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-230">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-231">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-232">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-233">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-234">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-235">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-236">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-237">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-238">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-239">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-240">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-241">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-242">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-243">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-244">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-245">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-246">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-247">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-248">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-249">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-250">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-251">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-252">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-253">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-254">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-255">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-256">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-257">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-258">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-259">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-259">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="88a6c-260">A serialização do .NET Framework para o .NET Core não é suportada.</span><span class="sxs-lookup"><span data-stu-id="88a6c-260">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-261">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-261">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-262">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-262">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-263">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-264">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-265">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-266">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-267">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-268">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-269">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-270">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-271">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-272">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-273">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-274">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-275">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-276">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-277">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-278">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-279">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-280">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-281">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-281">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="88a6c-282">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-283">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-283">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-284">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-285">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-286">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-286">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="88a6c-287">Dados de serialização limitados.</span><span class="sxs-lookup"><span data-stu-id="88a6c-287">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-288">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-288">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-289">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-289">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-290">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-291">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-292">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-293">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-294">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-295">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-296">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-297">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-298">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-299">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-300">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-301">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-302">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-303">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-304">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-305">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-306">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-307">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-308">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-309">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-310">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-311">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-312">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-313">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-314">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-315">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-316">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-317">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-318">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-319">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-320">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="88a6c-321">Não serializável no .NET Framework 4.7 e nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="88a6c-321">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-322">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-323">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-323">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-324">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-325">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-326">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-327">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="88a6c-328">Começando em .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="88a6c-328">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="88a6c-329">Confira também</span><span class="sxs-lookup"><span data-stu-id="88a6c-329">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="88a6c-330">Contém classes que podem ser usadas para serialização e desserialização de objetos.</span><span class="sxs-lookup"><span data-stu-id="88a6c-330">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="88a6c-331">[Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="88a6c-331">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="88a6c-332">Descreve o mecanismo de serialização de XML que está incluído com o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="88a6c-332">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="88a6c-333">[Segurança e Serialização](../../../docs/framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="88a6c-333">[Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="88a6c-334">Descreve as diretrizes para codificação segura para seguir ao escrever o código que executa a serialização.</span><span class="sxs-lookup"><span data-stu-id="88a6c-334">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="88a6c-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="88a6c-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="88a6c-336">Descreve os vários métodos A partir do .NET Framework para comunicações remotas.</span><span class="sxs-lookup"><span data-stu-id="88a6c-336">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="88a6c-337">[Serviços web XML criados usando clientes de serviços web ASP.NET e XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="88a6c-337">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="88a6c-338">Artigos que descrevem e explicam como programar os serviços Web XML criados usando ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="88a6c-338">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
