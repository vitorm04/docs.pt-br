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
ms.author: mairaw
ms.openlocfilehash: 63158dd2dda5388870d3d5878fe29cb004aec401
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="binary-serialization"></a>Serialização binária

A serialização pode ser definida como o processo de armazenar o estado de um objeto em uma mídia de armazenamento. Durante esse processo, os campos públicos e privados do objeto e o nome da classe, incluindo o assembly que contém a classe, são convertidos em um fluxo de bytes, que é em seguida escrito em um fluxo de dados. Quando o objeto é desserializado posteriormente, um clone exato do objeto original é criado.

Ao implementar um mecanismo de serialização em um ambiente orientado a objeto, você precisará fazer algumas trocas entre a facilidade de uso e a flexibilidade. O processo pode ser automatizado em grande parte, contanto que você tenha controle suficiente sobre o processo. Por exemplo, em algumas situações, a serialização binária simples pode não ser suficiente, ou pode haver um motivo específico para decidir quais campos em uma classe precisam ser serializados. As seções a seguir examinam o mecanismo de serialização robusto fornecido com o .NET e destacam vários recursos importantes que permitem personalizar o processo para atender às suas necessidades.

> [!NOTE]
> O estado de um objeto codificado UTF-8 ou UTF-7 não é preservado se o objeto é serializado e desserializado usando versões diferentes do .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Como a natureza da serialização binária permite a modificação de membros particulares dentro de um objeto e, portanto, a alteração do estado dele, outras estruturas de serialização, como JSON.NET, que operam na superfície de API pública são recomendadas.

## <a name="binary-serialization-in-net-core"></a>Serialização binária no .NET Core

O .NET Core dá suporte à serialização binária com um subconjunto de tipos. Veja a lista de tipos com suporte na [seção Tipos serializáveis](#serializable-types). O conjunto definido de tipos têm a garantia de serem serializáveis entre o .NET Framework 4.5.1 e versões posteriores e o .NET Core 2.0 e versões posteriores. Outras implementações do .NET, como o Mono, não têm suporte oficial, mas também devem estar funcionando.

### <a name="serializable-types"></a>Tipos serializáveis

- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.AccessViolationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.AggregateException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ApplicationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ArgumentException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ArgumentNullException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ArithmeticException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.BadImageFormatException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- `System.Collections.Generic.NonRandomizedStringEqualityComparer` <!--zz <xref:System.Collections.Generic.NonRandomizedStringEqualityComparer?displayProperty=nameWithType> --> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores, a serialização do .NET Framework para .NET Core não é suportada)
- <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ContextMarshalException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DBNull?displayProperty=nameWithType> (disponível no .NET Core 2.0.2 e versões posteriores)   
- <xref:System.Data.Common.DbException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.ConstraintException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.DataException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.DataSet?displayProperty=nameWithType>
- <xref:System.Data.DataTable?displayProperty=nameWithType> (a menos que você defina RemotingFormat SerializationFormat.Binary caso em que ele pode ser trocado com o .NET Core 2.1 e versões posteriores.)   
- <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.EvaluateException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores, a serialização do .NET Framework para .NET Core não é suportada)
- <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.StrongTypingException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DataMisalignedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- `System.Diagnostics.Contracts.ContractException` <!--zz <xref:System.Diagnostics.Contracts.ContractException?displayProperty=nameWithType> --> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DivideByZeroException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.DllNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.EventArgs?displayProperty=nameWithType> (disponível no .NET Core 2.0.6 e versões posteriores)
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.ExecutionEngineException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.FieldAccessException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.FormatException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- `System.IO.Compression.ZLibException` <!--zz <xref:System.IO.Compression.ZLibException?displayProperty=nameWithType --> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.FileFormatException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.FileLoadException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.IOException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.InvalidDataException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.InsufficientMemoryException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.InvalidCastException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.InvalidOperationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.InvalidProgramException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.MemberAccessException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.MethodAccessException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.MissingFieldException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.MissingMemberException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.MissingMethodException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Net.CookieException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.HttpListenerException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.WebException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.NotFiniteNumberException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.NotImplementedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.NotSupportedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.NullReferenceException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.ObjectDisposedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.OperationCanceledException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.OutOfMemoryException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.OverflowException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.RankException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores, a serialização do .NET Framework para .NET Core não é suportada)
- <xref:System.Reflection.TargetException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` <!--zz <xref:System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException?displayProperty=nameWithType --> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.HostProtectionException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.SecurityException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores, dados de serialização limitado)
- <xref:System.Security.VerificationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.StackOverflowException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.SystemException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.TimeoutException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Transactions.TransactionException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.TypeAccessException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.TypeInitializationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.TypeLoadException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.TypeUnloadedException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Uri?displayProperty=nameWithType>   
- <xref:System.UriFormatException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.ValueTuple?displayProperty=nameWithType> (não é serializável em .NET Framework 4.7 e versões anteriores)  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Xml.XmlException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)
- <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> (disponível no .NET Core 2.0.4 e versões posteriores)

## <a name="in-this-section"></a>Nesta seção

 [Conceitos de serialização](../../../docs/standard/serialization/serialization-concepts.md)  
 Descreve dois cenários em que a serialização é útil: ao persistir dados para armazenamento e ao passar objetos entre domínios de aplicativo.  
  
 [Serialização básica](../../../docs/standard/serialization/basic-serialization.md)  
 Descreve como usar formatadores binários e SOAP para serializar objetos.  
  
 [Serialização seletiva](../../../docs/standard/serialization/selective-serialization.md)  
 Descreve como impedir que alguns membros de uma classe sejam serializados.  
  
 [Serialização personalizada](../../../docs/standard/serialization/custom-serialization.md)  
 Descreve como personalizar a serialização para uma classe usando a interface <xref:System.Runtime.Serialization.ISerializable>.  
  
 [Etapas no processo de serialização](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 Descreve o curso de ação que a serialização utiliza quando o método <xref:System.Runtime.Serialization.Formatter.Serialize%2A> é chamado em um formatador.  
  
 [Serialização tolerante a versão](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 Explica como criar tipos serializados que podem ser modificados ao longo do tempo sem fazer os aplicativos gerarem exceções.  
  
 [Diretrizes de serialização](../../../docs/standard/serialization/serialization-guidelines.md)  
 Fornece algumas diretrizes gerais para decidir quando serializar um objeto.  
  
## <a name="reference"></a>Referência  
 <xref:System.Runtime.Serialization>  
 Contém classes que podem ser usadas para serialização e desserialização de objetos.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Descreve o mecanismo de serialização de XML que está incluído com o Common Language Runtime.  
  
 [Segurança e serialização](../../../docs/framework/misc/security-and-serialization.md)  
 Descreve as diretrizes para codificação segura para seguir ao escrever o código que executa a serialização.  
  
 [Objetos remotos](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
 Descreve os vários métodos de comunicação disponíveis no .NET Framework para comunicações remotas.  
  
 [Serviços Web XML criados com o ASP.NET e clientes de serviços Web XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
 Fornece tópicos que descrevem e explicam como programar serviços Web XML criados usando o ASP.NET.
