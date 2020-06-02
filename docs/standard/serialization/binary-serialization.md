---
title: Serialização binária
description: Este artigo descreve a serialização binária e os tipos para os quais o .NET Core dá suporte. Lembre-se dos perigos de serialização binária e alternativas para ele.
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
ms.openlocfilehash: c735d30920fd3c8cd13243b4a5a29489ce05b262
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289688"
---
# <a name="binary-serialization"></a><span data-ttu-id="14779-104">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="14779-104">Binary serialization</span></span>

<span data-ttu-id="14779-105">A serialização pode ser definida como o processo de armazenar o estado de um objeto em uma mídia de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="14779-105">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="14779-106">Durante esse processo, os campos públicos e privados do objeto e o nome da classe, incluindo o assembly que contém a classe, são convertidos em um fluxo de bytes, que é em seguida escrito em um fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="14779-106">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="14779-107">Quando o objeto é desserializado posteriormente, um clone exato do objeto original é criado.</span><span class="sxs-lookup"><span data-stu-id="14779-107">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="14779-108">Ao implementar um mecanismo de serialização em um ambiente orientado a objeto, você precisará fazer algumas trocas entre a facilidade de uso e a flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="14779-108">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="14779-109">O processo pode ser automatizado em grande parte, contanto que você tenha controle suficiente sobre o processo.</span><span class="sxs-lookup"><span data-stu-id="14779-109">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="14779-110">Por exemplo, em algumas situações, a serialização binária simples pode não ser suficiente, ou pode haver um motivo específico para decidir quais campos em uma classe precisam ser serializados.</span><span class="sxs-lookup"><span data-stu-id="14779-110">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="14779-111">As seções a seguir examinam o mecanismo de serialização robusto fornecido com o .NET e destacam vários recursos importantes que permitem personalizar o processo para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="14779-111">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="14779-112">O estado de um objeto codificado UTF-8 ou UTF-7 não é preservado se o objeto é serializado e desserializado usando versões diferentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14779-112">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="14779-113">A serialização binária permite modificar membros privados dentro de um objeto e, portanto, alterar o estado dele.</span><span class="sxs-lookup"><span data-stu-id="14779-113">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="14779-114">Por isso, são recomendadas outras estruturas de serialização, como <xref:System.Text.Json?displayProperty=fullName> , que operam na superfície da API pública.</span><span class="sxs-lookup"><span data-stu-id="14779-114">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="14779-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="14779-115">.NET Core</span></span>

<span data-ttu-id="14779-116">O .NET Core dá suporte à serialização binária para um subconjunto de tipos.</span><span class="sxs-lookup"><span data-stu-id="14779-116">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="14779-117">Você pode ver a lista de tipos com suporte na seção [tipos serializáveis](#serializable-types) a seguir.</span><span class="sxs-lookup"><span data-stu-id="14779-117">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="14779-118">Os tipos listados têm a garantia de serem serializáveis entre .NET Framework 4.5.1 e versões posteriores e entre o .NET Core 2,0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="14779-118">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="14779-119">Outras implementações do .NET, como mono, não são oficialmente suportadas, mas também devem funcionar.</span><span class="sxs-lookup"><span data-stu-id="14779-119">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="14779-120">Tipos serializáveis</span><span class="sxs-lookup"><span data-stu-id="14779-120">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="14779-121">Type</span><span class="sxs-lookup"><span data-stu-id="14779-121">Type</span></span> | <span data-ttu-id="14779-122">Observações</span><span class="sxs-lookup"><span data-stu-id="14779-122">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="14779-123">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="14779-124">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="14779-125">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="14779-126">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="14779-127">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="14779-128">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="14779-129">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="14779-130">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="14779-131">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="14779-132">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="14779-133">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="14779-134">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="14779-135">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-136">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-136">Starting in .NET Core 2.0.4.</span></span> |
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
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="14779-137">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="14779-138">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="14779-139">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="14779-140">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-140">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="14779-141">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-141">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="14779-142">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-142">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="14779-143">Não há suporte para a serialização de .NET Framework para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="14779-143">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="14779-144">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="14779-145">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="14779-146">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="14779-147">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="14779-148">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="14779-149">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-150">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="14779-151">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-151">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="14779-152">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="14779-153">A partir do .NET Core 2.0.2 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="14779-153">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="14779-154">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="14779-155">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="14779-156">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-156">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="14779-157">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="14779-158">Se você definir `RemotingFormat` como `SerializationFormat.Binary` , ele só poderá ser trocado com o .net Core 2,1 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="14779-158">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="14779-159">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="14779-160">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="14779-161">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="14779-162">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="14779-163">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="14779-164">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="14779-165">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="14779-166">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="14779-167">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="14779-168">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="14779-169">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-169">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="14779-170">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-170">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="14779-171">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-171">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="14779-172">Não há suporte para a serialização de .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="14779-172">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="14779-173">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="14779-174">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="14779-175">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="14779-176">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="14779-177">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="14779-178">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="14779-179">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-180">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="14779-181">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="14779-182">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="14779-183">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-184">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="14779-185">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="14779-186">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="14779-187">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="14779-188">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="14779-189">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="14779-190">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="14779-191">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="14779-192">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-193">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="14779-194">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="14779-195">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="14779-196">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="14779-197">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="14779-198">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="14779-199">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="14779-200">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="14779-201">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="14779-202">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="14779-203">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="14779-204">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-205">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="14779-206">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-206">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-207">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="14779-208">A partir do .NET Core 2.0.6.</span><span class="sxs-lookup"><span data-stu-id="14779-208">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="14779-209">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="14779-210">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="14779-211">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-212">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="14779-213">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-214">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="14779-215">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="14779-216">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="14779-217">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-218">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="14779-219">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="14779-220">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="14779-221">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="14779-222">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="14779-223">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="14779-224">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="14779-225">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="14779-226">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="14779-227">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="14779-228">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="14779-229">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="14779-230">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="14779-231">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="14779-232">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="14779-233">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="14779-234">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="14779-235">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="14779-236">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="14779-237">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="14779-238">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="14779-239">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="14779-240">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="14779-241">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="14779-242">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="14779-243">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="14779-244">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="14779-245">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="14779-246">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="14779-247">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="14779-248">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="14779-249">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="14779-250">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="14779-251">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="14779-252">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="14779-253">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="14779-254">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="14779-255">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="14779-256">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="14779-257">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="14779-258">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="14779-259">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-259">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="14779-260">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-260">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="14779-261">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-261">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="14779-262">Não há suporte para a serialização de .NET Framework para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="14779-262">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="14779-263">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="14779-264">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="14779-265">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="14779-266">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="14779-267">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="14779-268">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="14779-269">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="14779-270">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="14779-271">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="14779-272">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="14779-273">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="14779-274">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="14779-275">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="14779-276">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="14779-277">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="14779-278">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="14779-279">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="14779-280">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="14779-281">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-281">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="14779-282">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="14779-283">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-283">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="14779-284">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="14779-285">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="14779-286">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-286">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="14779-287">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-287">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="14779-288">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-288">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="14779-289">Dados de serialização limitados.</span><span class="sxs-lookup"><span data-stu-id="14779-289">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="14779-290">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="14779-291">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="14779-292">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="14779-293">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="14779-294">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="14779-295">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="14779-296">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="14779-297">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="14779-298">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="14779-299">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="14779-300">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="14779-301">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="14779-302">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="14779-303">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="14779-304">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="14779-305">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="14779-306">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="14779-307">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="14779-308">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="14779-309">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="14779-310">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="14779-311">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="14779-312">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="14779-313">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="14779-314">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="14779-315">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="14779-316">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="14779-317">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="14779-318">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="14779-319">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="14779-320">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="14779-321">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-321">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="14779-322">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="14779-323">Não serializável no .NET Framework 4,7 e em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="14779-323">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="14779-324">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="14779-325">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="14779-326">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="14779-327">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="14779-328">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-328">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="14779-329">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-329">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="14779-330">A partir do .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="14779-330">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="14779-331">Veja também</span><span class="sxs-lookup"><span data-stu-id="14779-331">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="14779-332">Contém classes que podem ser usadas para serialização e desserialização de objetos.</span><span class="sxs-lookup"><span data-stu-id="14779-332">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="14779-333">[Serialização de XML e SOAP](xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="14779-333">[XML and SOAP Serialization](xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="14779-334">Descreve o mecanismo de serialização de XML que está incluído com o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="14779-334">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="14779-335">[Segurança e serialização](../../framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="14779-335">[Security and Serialization](../../framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="14779-336">Descreve as diretrizes para codificação segura para seguir ao escrever o código que executa a serialização.</span><span class="sxs-lookup"><span data-stu-id="14779-336">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="14779-337">[Comunicação remota do .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="14779-337">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="14779-338">Descreve os vários métodos que começam no .NET Framework para comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="14779-338">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="14779-339">[Serviços Web XML criados usando ASP.NET e clientes de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="14779-339">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="14779-340">Artigos que descrevem e explicam como programar serviços Web XML criados usando o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="14779-340">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
