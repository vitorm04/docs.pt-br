---
title: "Coleções de esquema de banco de dados OLE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="6d8f6-102">Coleções de esquema de banco de dados OLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="6d8f6-103">Esta seção discute o suporte de coleção de esquema para os provedores OLE DB para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="6d8f6-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="6d8f6-104">Provedor Microsoft SQL Server, OLE DB</span><span class="sxs-lookup"><span data-stu-id="6d8f6-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="6d8f6-105">O Microsoft OLE DB Driver do SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="6d8f6-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6d8f6-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-106">Tables</span></span>  
  
-   <span data-ttu-id="6d8f6-107">Colunas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-107">Columns</span></span>  
  
-   <span data-ttu-id="6d8f6-108">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6d8f6-108">Procedures</span></span>  
  
-   <span data-ttu-id="6d8f6-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6d8f6-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="6d8f6-110">Catálogo</span><span class="sxs-lookup"><span data-stu-id="6d8f6-110">Catalog</span></span>  
  
-   <span data-ttu-id="6d8f6-111">Índices</span><span class="sxs-lookup"><span data-stu-id="6d8f6-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6d8f6-112">Tabelas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-112">Tables</span></span>  
  
|<span data-ttu-id="6d8f6-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-113">ColumnName</span></span>|<span data-ttu-id="6d8f6-114">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-115">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-116">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-116">String</span></span>|  
|<span data-ttu-id="6d8f6-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-118">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-118">String</span></span>|  
|<span data-ttu-id="6d8f6-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-119">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-120">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-120">String</span></span>|  
|<span data-ttu-id="6d8f6-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-121">TABLE_TYPE</span></span>|<span data-ttu-id="6d8f6-122">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-122">String</span></span>|  
|<span data-ttu-id="6d8f6-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-123">TABLE_GUID</span></span>|<span data-ttu-id="6d8f6-124">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-124">Guid</span></span>|  
|<span data-ttu-id="6d8f6-125">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-125">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-126">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-126">String</span></span>|  
|<span data-ttu-id="6d8f6-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-127">TABLE_PROPID</span></span>|<span data-ttu-id="6d8f6-128">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-128">Int64</span></span>|  
|<span data-ttu-id="6d8f6-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-129">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-130">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-131">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6d8f6-133">Colunas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-133">Columns</span></span>  
  
|<span data-ttu-id="6d8f6-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-134">ColumnName</span></span>|<span data-ttu-id="6d8f6-135">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-136">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-137">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-137">String</span></span>|  
|<span data-ttu-id="6d8f6-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-139">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-139">String</span></span>|  
|<span data-ttu-id="6d8f6-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-140">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-141">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-141">String</span></span>|  
|<span data-ttu-id="6d8f6-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-142">COLUMN_NAME</span></span>|<span data-ttu-id="6d8f6-143">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-143">String</span></span>|  
|<span data-ttu-id="6d8f6-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-144">COLUMN_GUID</span></span>|<span data-ttu-id="6d8f6-145">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-145">Guid</span></span>|  
|<span data-ttu-id="6d8f6-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-146">COLUMN_PROPID</span></span>|<span data-ttu-id="6d8f6-147">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-147">Int64</span></span>|  
|<span data-ttu-id="6d8f6-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-149">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-149">Int64</span></span>|  
|<span data-ttu-id="6d8f6-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6d8f6-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-151">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6d8f6-153">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-153">String</span></span>|  
|<span data-ttu-id="6d8f6-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="6d8f6-155">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-155">Int64</span></span>|  
|<span data-ttu-id="6d8f6-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-156">IS_NULLABLE</span></span>|<span data-ttu-id="6d8f6-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-157">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-158">DATA_TYPE</span></span>|<span data-ttu-id="6d8f6-159">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-159">Int32</span></span>|  
|<span data-ttu-id="6d8f6-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-160">TYPE_GUID</span></span>|<span data-ttu-id="6d8f6-161">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-161">Guid</span></span>|  
|<span data-ttu-id="6d8f6-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d8f6-163">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-163">Int64</span></span>|  
|<span data-ttu-id="6d8f6-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d8f6-165">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-165">Int64</span></span>|  
|<span data-ttu-id="6d8f6-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d8f6-167">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-167">Int32</span></span>|  
|<span data-ttu-id="6d8f6-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d8f6-169">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-169">Int16</span></span>|  
|<span data-ttu-id="6d8f6-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="6d8f6-171">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-171">Int64</span></span>|  
|<span data-ttu-id="6d8f6-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6d8f6-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-173">String</span></span>|  
|<span data-ttu-id="6d8f6-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6d8f6-175">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-175">String</span></span>|  
|<span data-ttu-id="6d8f6-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6d8f6-177">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-177">String</span></span>|  
|<span data-ttu-id="6d8f6-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="6d8f6-179">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-179">String</span></span>|  
|<span data-ttu-id="6d8f6-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6d8f6-181">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-181">String</span></span>|  
|<span data-ttu-id="6d8f6-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-182">COLLATION_NAME</span></span>|<span data-ttu-id="6d8f6-183">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-183">String</span></span>|  
|<span data-ttu-id="6d8f6-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6d8f6-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-185">String</span></span>|  
|<span data-ttu-id="6d8f6-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6d8f6-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-187">String</span></span>|  
|<span data-ttu-id="6d8f6-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-188">DOMAIN_NAME</span></span>|<span data-ttu-id="6d8f6-189">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-189">String</span></span>|  
|<span data-ttu-id="6d8f6-190">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-190">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-191">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-191">String</span></span>|  
|<span data-ttu-id="6d8f6-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-192">COLUMN_LCID</span></span>|<span data-ttu-id="6d8f6-193">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-193">Int32</span></span>|  
|<span data-ttu-id="6d8f6-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="6d8f6-195">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-195">Int32</span></span>|  
|<span data-ttu-id="6d8f6-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-196">COLUMN_SORTID</span></span>|<span data-ttu-id="6d8f6-197">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-197">Int32</span></span>|  
|<span data-ttu-id="6d8f6-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="6d8f6-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="6d8f6-199">Byte[]</span></span>|  
|<span data-ttu-id="6d8f6-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-200">IS_COMPUTED</span></span>|<span data-ttu-id="6d8f6-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6d8f6-202">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6d8f6-202">Procedures</span></span>  
  
|<span data-ttu-id="6d8f6-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-203">ColumnName</span></span>|<span data-ttu-id="6d8f6-204">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d8f6-206">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-206">String</span></span>|  
|<span data-ttu-id="6d8f6-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-208">String</span></span>|  
|<span data-ttu-id="6d8f6-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d8f6-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-210">String</span></span>|  
|<span data-ttu-id="6d8f6-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6d8f6-212">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-212">Int16</span></span>|  
|<span data-ttu-id="6d8f6-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6d8f6-214">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-214">String</span></span>|  
|<span data-ttu-id="6d8f6-215">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-215">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-216">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-216">String</span></span>|  
|<span data-ttu-id="6d8f6-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-217">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-218">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-219">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="6d8f6-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6d8f6-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="6d8f6-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-222">ColumnName</span></span>|<span data-ttu-id="6d8f6-223">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d8f6-225">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-225">String</span></span>|  
|<span data-ttu-id="6d8f6-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-227">String</span></span>|  
|<span data-ttu-id="6d8f6-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d8f6-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-229">String</span></span>|  
|<span data-ttu-id="6d8f6-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-230">PARAMETER_NAME</span></span>|<span data-ttu-id="6d8f6-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-231">String</span></span>|  
|<span data-ttu-id="6d8f6-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-233">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-233">Int32</span></span>|  
|<span data-ttu-id="6d8f6-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="6d8f6-235">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-235">Int32</span></span>|  
|<span data-ttu-id="6d8f6-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="6d8f6-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-237">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="6d8f6-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-239">String</span></span>|  
|<span data-ttu-id="6d8f6-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-240">IS_NULLABLE</span></span>|<span data-ttu-id="6d8f6-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-241">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-242">DATA_TYPE</span></span>|<span data-ttu-id="6d8f6-243">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-243">Int32</span></span>|  
|<span data-ttu-id="6d8f6-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d8f6-245">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-245">Int64</span></span>|  
|<span data-ttu-id="6d8f6-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d8f6-247">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-247">Int64</span></span>|  
|<span data-ttu-id="6d8f6-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d8f6-249">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-249">Int32</span></span>|  
|<span data-ttu-id="6d8f6-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d8f6-251">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-251">Int16</span></span>|  
|<span data-ttu-id="6d8f6-252">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-252">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-253">String</span></span>|  
|<span data-ttu-id="6d8f6-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-254">TYPE_NAME</span></span>|<span data-ttu-id="6d8f6-255">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-255">String</span></span>|  
|<span data-ttu-id="6d8f6-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="6d8f6-257">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="6d8f6-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="6d8f6-258">Catalog</span></span>  
  
|<span data-ttu-id="6d8f6-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-259">ColumnName</span></span>|<span data-ttu-id="6d8f6-260">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-261">CATALOG_NAME</span></span>|<span data-ttu-id="6d8f6-262">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-262">String</span></span>|  
|<span data-ttu-id="6d8f6-263">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-263">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-264">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6d8f6-265">Índices</span><span class="sxs-lookup"><span data-stu-id="6d8f6-265">Indexes</span></span>  
  
|<span data-ttu-id="6d8f6-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-266">ColumnName</span></span>|<span data-ttu-id="6d8f6-267">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-268">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-269">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-269">String</span></span>|  
|<span data-ttu-id="6d8f6-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-271">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-271">String</span></span>|  
|<span data-ttu-id="6d8f6-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-272">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-273">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-273">String</span></span>|  
|<span data-ttu-id="6d8f6-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-274">INDEX_CATALOG</span></span>|<span data-ttu-id="6d8f6-275">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-275">String</span></span>|  
|<span data-ttu-id="6d8f6-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="6d8f6-277">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-277">String</span></span>|  
|<span data-ttu-id="6d8f6-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-278">INDEX_NAME</span></span>|<span data-ttu-id="6d8f6-279">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-279">String</span></span>|  
|<span data-ttu-id="6d8f6-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6d8f6-280">PRIMARY_KEY</span></span>|<span data-ttu-id="6d8f6-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-281">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-282">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-282">UNIQUE</span></span>|<span data-ttu-id="6d8f6-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-283">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-284">CLUSTERED</span></span>|<span data-ttu-id="6d8f6-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-285">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-286">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-286">TYPE</span></span>|<span data-ttu-id="6d8f6-287">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-287">Int32</span></span>|  
|<span data-ttu-id="6d8f6-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6d8f6-288">FILL_FACTOR</span></span>|<span data-ttu-id="6d8f6-289">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-289">Int32</span></span>|  
|<span data-ttu-id="6d8f6-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-290">INITIAL_SIZE</span></span>|<span data-ttu-id="6d8f6-291">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-291">Int32</span></span>|  
|<span data-ttu-id="6d8f6-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-292">NULLS</span></span>|<span data-ttu-id="6d8f6-293">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-293">Int32</span></span>|  
|<span data-ttu-id="6d8f6-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6d8f6-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-295">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-296">AUTO_UPDATE</span></span>|<span data-ttu-id="6d8f6-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-297">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-298">NULL_COLLATION</span></span>|<span data-ttu-id="6d8f6-299">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-299">Int32</span></span>|  
|<span data-ttu-id="6d8f6-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-301">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-301">Int64</span></span>|  
|<span data-ttu-id="6d8f6-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-302">COLUMN_NAME</span></span>|<span data-ttu-id="6d8f6-303">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-303">String</span></span>|  
|<span data-ttu-id="6d8f6-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-304">COLUMN_GUID</span></span>|<span data-ttu-id="6d8f6-305">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-305">Guid</span></span>|  
|<span data-ttu-id="6d8f6-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-306">COLUMN_PROPID</span></span>|<span data-ttu-id="6d8f6-307">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-307">Int64</span></span>|  
|<span data-ttu-id="6d8f6-308">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-308">COLLATION</span></span>|<span data-ttu-id="6d8f6-309">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-309">Int16</span></span>|  
|<span data-ttu-id="6d8f6-310">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-310">CARDINALITY</span></span>|<span data-ttu-id="6d8f6-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="6d8f6-311">Decimal</span></span>|  
|<span data-ttu-id="6d8f6-312">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-312">PAGES</span></span>|<span data-ttu-id="6d8f6-313">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-313">Int32</span></span>|  
|<span data-ttu-id="6d8f6-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-314">FILTER_CONDITION</span></span>|<span data-ttu-id="6d8f6-315">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-315">String</span></span>|  
|<span data-ttu-id="6d8f6-316">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-316">INTEGRATED</span></span>|<span data-ttu-id="6d8f6-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="6d8f6-318">Provedor OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="6d8f6-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="6d8f6-319">O Microsoft OLE DB Driver Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="6d8f6-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6d8f6-320">Tabelas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-320">Tables</span></span>  
  
-   <span data-ttu-id="6d8f6-321">Colunas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-321">Columns</span></span>  
  
-   <span data-ttu-id="6d8f6-322">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6d8f6-322">Procedures</span></span>  
  
-   <span data-ttu-id="6d8f6-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6d8f6-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="6d8f6-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6d8f6-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="6d8f6-325">Exibições</span><span class="sxs-lookup"><span data-stu-id="6d8f6-325">Views</span></span>  
  
-   <span data-ttu-id="6d8f6-326">Índices</span><span class="sxs-lookup"><span data-stu-id="6d8f6-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6d8f6-327">Tabelas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-327">Tables</span></span>  
  
|<span data-ttu-id="6d8f6-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-328">ColumnName</span></span>|<span data-ttu-id="6d8f6-329">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-330">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-331">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-331">String</span></span>|  
|<span data-ttu-id="6d8f6-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-333">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-333">String</span></span>|  
|<span data-ttu-id="6d8f6-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-334">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-335">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-335">String</span></span>|  
|<span data-ttu-id="6d8f6-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-336">TABLE_TYPE</span></span>|<span data-ttu-id="6d8f6-337">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-337">String</span></span>|  
|<span data-ttu-id="6d8f6-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-338">TABLE_GUID</span></span>|<span data-ttu-id="6d8f6-339">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-339">Guid</span></span>|  
|<span data-ttu-id="6d8f6-340">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-340">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-341">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-341">String</span></span>|  
|<span data-ttu-id="6d8f6-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-342">TABLE_PROPID</span></span>|<span data-ttu-id="6d8f6-343">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-343">Int64</span></span>|  
|<span data-ttu-id="6d8f6-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-344">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-345">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-346">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6d8f6-348">Colunas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-348">Columns</span></span>  
  
|<span data-ttu-id="6d8f6-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-349">ColumnName</span></span>|<span data-ttu-id="6d8f6-350">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-351">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-352">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-352">String</span></span>|  
|<span data-ttu-id="6d8f6-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-354">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-354">String</span></span>|  
|<span data-ttu-id="6d8f6-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-355">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-356">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-356">String</span></span>|  
|<span data-ttu-id="6d8f6-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-357">COLUMN_NAME</span></span>|<span data-ttu-id="6d8f6-358">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-358">String</span></span>|  
|<span data-ttu-id="6d8f6-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-359">COLUMN_GUID</span></span>|<span data-ttu-id="6d8f6-360">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-360">Guid</span></span>|  
|<span data-ttu-id="6d8f6-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-361">COLUMN_PROPID</span></span>|<span data-ttu-id="6d8f6-362">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-362">Int64</span></span>|  
|<span data-ttu-id="6d8f6-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-364">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-364">Int64</span></span>|  
|<span data-ttu-id="6d8f6-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6d8f6-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-366">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6d8f6-368">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-368">String</span></span>|  
|<span data-ttu-id="6d8f6-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="6d8f6-370">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-370">Int64</span></span>|  
|<span data-ttu-id="6d8f6-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-371">IS_NULLABLE</span></span>|<span data-ttu-id="6d8f6-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-372">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-373">DATA_TYPE</span></span>|<span data-ttu-id="6d8f6-374">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-374">Int32</span></span>|  
|<span data-ttu-id="6d8f6-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-375">TYPE_GUID</span></span>|<span data-ttu-id="6d8f6-376">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-376">Guid</span></span>|  
|<span data-ttu-id="6d8f6-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d8f6-378">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-378">Int64</span></span>|  
|<span data-ttu-id="6d8f6-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d8f6-380">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-380">Int64</span></span>|  
|<span data-ttu-id="6d8f6-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d8f6-382">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-382">Int32</span></span>|  
|<span data-ttu-id="6d8f6-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d8f6-384">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-384">Int16</span></span>|  
|<span data-ttu-id="6d8f6-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="6d8f6-386">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-386">Int64</span></span>|  
|<span data-ttu-id="6d8f6-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6d8f6-388">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-388">String</span></span>|  
|<span data-ttu-id="6d8f6-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6d8f6-390">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-390">String</span></span>|  
|<span data-ttu-id="6d8f6-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6d8f6-392">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-392">String</span></span>|  
|<span data-ttu-id="6d8f6-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="6d8f6-394">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-394">String</span></span>|  
|<span data-ttu-id="6d8f6-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6d8f6-396">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-396">String</span></span>|  
|<span data-ttu-id="6d8f6-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-397">COLLATION_NAME</span></span>|<span data-ttu-id="6d8f6-398">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-398">String</span></span>|  
|<span data-ttu-id="6d8f6-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6d8f6-400">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-400">String</span></span>|  
|<span data-ttu-id="6d8f6-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6d8f6-402">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-402">String</span></span>|  
|<span data-ttu-id="6d8f6-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-403">DOMAIN_NAME</span></span>|<span data-ttu-id="6d8f6-404">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-404">String</span></span>|  
|<span data-ttu-id="6d8f6-405">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-405">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-406">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6d8f6-407">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6d8f6-407">Procedures</span></span>  
  
|<span data-ttu-id="6d8f6-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-408">ColumnName</span></span>|<span data-ttu-id="6d8f6-409">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d8f6-411">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-411">String</span></span>|  
|<span data-ttu-id="6d8f6-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-413">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-413">String</span></span>|  
|<span data-ttu-id="6d8f6-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d8f6-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-415">String</span></span>|  
|<span data-ttu-id="6d8f6-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6d8f6-417">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-417">Int16</span></span>|  
|<span data-ttu-id="6d8f6-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6d8f6-419">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-419">String</span></span>|  
|<span data-ttu-id="6d8f6-420">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-420">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-421">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-421">String</span></span>|  
|<span data-ttu-id="6d8f6-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-422">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-423">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-424">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="6d8f6-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6d8f6-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="6d8f6-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-427">ColumnName</span></span>|<span data-ttu-id="6d8f6-428">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d8f6-430">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-430">String</span></span>|  
|<span data-ttu-id="6d8f6-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-432">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-432">String</span></span>|  
|<span data-ttu-id="6d8f6-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d8f6-434">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-434">String</span></span>|  
|<span data-ttu-id="6d8f6-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-435">COLUMN_NAME</span></span>|<span data-ttu-id="6d8f6-436">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-436">String</span></span>|  
|<span data-ttu-id="6d8f6-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-437">COLUMN_GUID</span></span>|<span data-ttu-id="6d8f6-438">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-438">Guid</span></span>|  
|<span data-ttu-id="6d8f6-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-439">COLUMN_PROPID</span></span>|<span data-ttu-id="6d8f6-440">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-440">Int64</span></span>|  
|<span data-ttu-id="6d8f6-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="6d8f6-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="6d8f6-442">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-442">Int64</span></span>|  
|<span data-ttu-id="6d8f6-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-444">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-444">Int64</span></span>|  
|<span data-ttu-id="6d8f6-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-445">IS_NULLABLE</span></span>|<span data-ttu-id="6d8f6-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-446">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-447">DATA_TYPE</span></span>|<span data-ttu-id="6d8f6-448">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-448">Int32</span></span>|  
|<span data-ttu-id="6d8f6-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-449">TYPE_GUID</span></span>|<span data-ttu-id="6d8f6-450">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-450">Guid</span></span>|  
|<span data-ttu-id="6d8f6-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d8f6-452">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-452">Int64</span></span>|  
|<span data-ttu-id="6d8f6-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d8f6-454">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-454">Int64</span></span>|  
|<span data-ttu-id="6d8f6-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d8f6-456">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-456">Int32</span></span>|  
|<span data-ttu-id="6d8f6-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d8f6-458">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-458">Int16</span></span>|  
|<span data-ttu-id="6d8f6-459">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-459">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-460">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-460">String</span></span>|  
|<span data-ttu-id="6d8f6-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="6d8f6-461">OVERLOAD</span></span>|<span data-ttu-id="6d8f6-462">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6d8f6-463">Exibições</span><span class="sxs-lookup"><span data-stu-id="6d8f6-463">Views</span></span>  
  
|<span data-ttu-id="6d8f6-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-464">ColumnName</span></span>|<span data-ttu-id="6d8f6-465">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-466">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-467">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-467">String</span></span>|  
|<span data-ttu-id="6d8f6-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-469">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-469">String</span></span>|  
|<span data-ttu-id="6d8f6-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-470">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-471">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-471">String</span></span>|  
|<span data-ttu-id="6d8f6-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="6d8f6-473">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-473">String</span></span>|  
|<span data-ttu-id="6d8f6-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-474">CHECK_OPTION</span></span>|<span data-ttu-id="6d8f6-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-475">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-476">IS_UPDATABLE</span></span>|<span data-ttu-id="6d8f6-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-477">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-478">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-478">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-479">String</span></span>|  
|<span data-ttu-id="6d8f6-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-480">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-481">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-482">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6d8f6-484">Índices</span><span class="sxs-lookup"><span data-stu-id="6d8f6-484">Indexes</span></span>  
  
|<span data-ttu-id="6d8f6-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-485">ColumnName</span></span>|<span data-ttu-id="6d8f6-486">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-487">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-488">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-488">String</span></span>|  
|<span data-ttu-id="6d8f6-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-490">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-490">String</span></span>|  
|<span data-ttu-id="6d8f6-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-491">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-492">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-492">String</span></span>|  
|<span data-ttu-id="6d8f6-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-493">INDEX_CATALOG</span></span>|<span data-ttu-id="6d8f6-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-494">String</span></span>|  
|<span data-ttu-id="6d8f6-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="6d8f6-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-496">String</span></span>|  
|<span data-ttu-id="6d8f6-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-497">INDEX_NAME</span></span>|<span data-ttu-id="6d8f6-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-498">String</span></span>|  
|<span data-ttu-id="6d8f6-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6d8f6-499">PRIMARY_KEY</span></span>|<span data-ttu-id="6d8f6-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-500">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-501">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-501">UNIQUE</span></span>|<span data-ttu-id="6d8f6-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-502">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-503">CLUSTERED</span></span>|<span data-ttu-id="6d8f6-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-504">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-505">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-505">TYPE</span></span>|<span data-ttu-id="6d8f6-506">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-506">Int32</span></span>|  
|<span data-ttu-id="6d8f6-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6d8f6-507">FILL_FACTOR</span></span>|<span data-ttu-id="6d8f6-508">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-508">Int32</span></span>|  
|<span data-ttu-id="6d8f6-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-509">INITIAL_SIZE</span></span>|<span data-ttu-id="6d8f6-510">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-510">Int32</span></span>|  
|<span data-ttu-id="6d8f6-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-511">NULLS</span></span>|<span data-ttu-id="6d8f6-512">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-512">Int32</span></span>|  
|<span data-ttu-id="6d8f6-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6d8f6-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-514">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-515">AUTO_UPDATE</span></span>|<span data-ttu-id="6d8f6-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-516">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-517">NULL_COLLATION</span></span>|<span data-ttu-id="6d8f6-518">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-518">Int32</span></span>|  
|<span data-ttu-id="6d8f6-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-520">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-520">Int64</span></span>|  
|<span data-ttu-id="6d8f6-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-521">COLUMN_NAME</span></span>|<span data-ttu-id="6d8f6-522">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-522">String</span></span>|  
|<span data-ttu-id="6d8f6-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-523">COLUMN_GUID</span></span>|<span data-ttu-id="6d8f6-524">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-524">Guid</span></span>|  
|<span data-ttu-id="6d8f6-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-525">COLUMN_PROPID</span></span>|<span data-ttu-id="6d8f6-526">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-526">Int64</span></span>|  
|<span data-ttu-id="6d8f6-527">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-527">COLLATION</span></span>|<span data-ttu-id="6d8f6-528">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-528">Int16</span></span>|  
|<span data-ttu-id="6d8f6-529">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-529">CARDINALITY</span></span>|<span data-ttu-id="6d8f6-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="6d8f6-530">Decimal</span></span>|  
|<span data-ttu-id="6d8f6-531">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-531">PAGES</span></span>|<span data-ttu-id="6d8f6-532">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-532">Int32</span></span>|  
|<span data-ttu-id="6d8f6-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-533">FILTER_CONDITION</span></span>|<span data-ttu-id="6d8f6-534">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-534">String</span></span>|  
|<span data-ttu-id="6d8f6-535">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-535">INTEGRATED</span></span>|<span data-ttu-id="6d8f6-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="6d8f6-537">Provedor do Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="6d8f6-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="6d8f6-538">O Microsoft Jet OLE DB Driver suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="6d8f6-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6d8f6-539">Tabelas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-539">Tables</span></span>  
  
-   <span data-ttu-id="6d8f6-540">Colunas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-540">Columns</span></span>  
  
-   <span data-ttu-id="6d8f6-541">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6d8f6-541">Procedures</span></span>  
  
-   <span data-ttu-id="6d8f6-542">Exibições</span><span class="sxs-lookup"><span data-stu-id="6d8f6-542">Views</span></span>  
  
-   <span data-ttu-id="6d8f6-543">Índices</span><span class="sxs-lookup"><span data-stu-id="6d8f6-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6d8f6-544">Tabelas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-544">Tables</span></span>  
  
|<span data-ttu-id="6d8f6-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-545">ColumnName</span></span>|<span data-ttu-id="6d8f6-546">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-547">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-548">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-548">String</span></span>|  
|<span data-ttu-id="6d8f6-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-550">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-550">String</span></span>|  
|<span data-ttu-id="6d8f6-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-551">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-552">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-552">String</span></span>|  
|<span data-ttu-id="6d8f6-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-553">TABLE_TYPE</span></span>|<span data-ttu-id="6d8f6-554">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-554">String</span></span>|  
|<span data-ttu-id="6d8f6-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-555">TABLE_GUID</span></span>|<span data-ttu-id="6d8f6-556">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-556">Guid</span></span>|  
|<span data-ttu-id="6d8f6-557">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-557">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-558">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-558">String</span></span>|  
|<span data-ttu-id="6d8f6-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-559">TABLE_PROPID</span></span>|<span data-ttu-id="6d8f6-560">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-560">Int64</span></span>|  
|<span data-ttu-id="6d8f6-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-561">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-562">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-563">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6d8f6-565">Colunas</span><span class="sxs-lookup"><span data-stu-id="6d8f6-565">Columns</span></span>  
  
|<span data-ttu-id="6d8f6-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-566">ColumnName</span></span>|<span data-ttu-id="6d8f6-567">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-568">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-569">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-569">String</span></span>|  
|<span data-ttu-id="6d8f6-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-571">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-571">String</span></span>|  
|<span data-ttu-id="6d8f6-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-572">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-573">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-573">String</span></span>|  
|<span data-ttu-id="6d8f6-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-574">COLUMN_NAME</span></span>|<span data-ttu-id="6d8f6-575">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-575">String</span></span>|  
|<span data-ttu-id="6d8f6-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-576">COLUMN_GUID</span></span>|<span data-ttu-id="6d8f6-577">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-577">Guid</span></span>|  
|<span data-ttu-id="6d8f6-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-578">COLUMN_PROPID</span></span>|<span data-ttu-id="6d8f6-579">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-579">Int64</span></span>|  
|<span data-ttu-id="6d8f6-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-581">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-581">Int64</span></span>|  
|<span data-ttu-id="6d8f6-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6d8f6-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-583">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d8f6-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6d8f6-585">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-585">String</span></span>|  
|<span data-ttu-id="6d8f6-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="6d8f6-587">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-587">Int64</span></span>|  
|<span data-ttu-id="6d8f6-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-588">IS_NULLABLE</span></span>|<span data-ttu-id="6d8f6-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-589">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-590">DATA_TYPE</span></span>|<span data-ttu-id="6d8f6-591">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-591">Int32</span></span>|  
|<span data-ttu-id="6d8f6-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-592">TYPE_GUID</span></span>|<span data-ttu-id="6d8f6-593">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-593">Guid</span></span>|  
|<span data-ttu-id="6d8f6-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d8f6-595">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-595">Int64</span></span>|  
|<span data-ttu-id="6d8f6-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d8f6-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d8f6-597">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-597">Int64</span></span>|  
|<span data-ttu-id="6d8f6-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d8f6-599">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-599">Int32</span></span>|  
|<span data-ttu-id="6d8f6-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d8f6-601">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-601">Int16</span></span>|  
|<span data-ttu-id="6d8f6-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="6d8f6-603">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-603">Int64</span></span>|  
|<span data-ttu-id="6d8f6-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6d8f6-605">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-605">String</span></span>|  
|<span data-ttu-id="6d8f6-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6d8f6-607">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-607">String</span></span>|  
|<span data-ttu-id="6d8f6-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6d8f6-609">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-609">String</span></span>|  
|<span data-ttu-id="6d8f6-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="6d8f6-611">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-611">String</span></span>|  
|<span data-ttu-id="6d8f6-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6d8f6-613">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-613">String</span></span>|  
|<span data-ttu-id="6d8f6-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-614">COLLATION_NAME</span></span>|<span data-ttu-id="6d8f6-615">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-615">String</span></span>|  
|<span data-ttu-id="6d8f6-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6d8f6-617">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-617">String</span></span>|  
|<span data-ttu-id="6d8f6-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6d8f6-619">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-619">String</span></span>|  
|<span data-ttu-id="6d8f6-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-620">DOMAIN_NAME</span></span>|<span data-ttu-id="6d8f6-621">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-621">String</span></span>|  
|<span data-ttu-id="6d8f6-622">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-622">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-623">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6d8f6-624">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6d8f6-624">Procedures</span></span>  
  
|<span data-ttu-id="6d8f6-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-625">ColumnName</span></span>|<span data-ttu-id="6d8f6-626">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d8f6-628">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-628">String</span></span>|  
|<span data-ttu-id="6d8f6-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-630">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-630">String</span></span>|  
|<span data-ttu-id="6d8f6-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d8f6-632">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-632">String</span></span>|  
|<span data-ttu-id="6d8f6-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6d8f6-634">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-634">Int16</span></span>|  
|<span data-ttu-id="6d8f6-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6d8f6-636">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-636">String</span></span>|  
|<span data-ttu-id="6d8f6-637">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-637">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-638">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-638">String</span></span>|  
|<span data-ttu-id="6d8f6-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-639">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-640">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-641">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6d8f6-643">Exibições</span><span class="sxs-lookup"><span data-stu-id="6d8f6-643">Views</span></span>  
  
|<span data-ttu-id="6d8f6-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-644">ColumnName</span></span>|<span data-ttu-id="6d8f6-645">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-646">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-647">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-647">String</span></span>|  
|<span data-ttu-id="6d8f6-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-649">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-649">String</span></span>|  
|<span data-ttu-id="6d8f6-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-650">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-651">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-651">String</span></span>|  
|<span data-ttu-id="6d8f6-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="6d8f6-653">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-653">String</span></span>|  
|<span data-ttu-id="6d8f6-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-654">CHECK_OPTION</span></span>|<span data-ttu-id="6d8f6-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-655">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-656">IS_UPDATABLE</span></span>|<span data-ttu-id="6d8f6-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-657">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-658">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-658">DESCRIPTION</span></span>|<span data-ttu-id="6d8f6-659">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-659">String</span></span>|  
|<span data-ttu-id="6d8f6-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-660">DATE_CREATED</span></span>|<span data-ttu-id="6d8f6-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-661">DateTime</span></span>|  
|<span data-ttu-id="6d8f6-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-662">DATE_MODIFIED</span></span>|<span data-ttu-id="6d8f6-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8f6-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6d8f6-664">Índices</span><span class="sxs-lookup"><span data-stu-id="6d8f6-664">Indexes</span></span>  
  
|<span data-ttu-id="6d8f6-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="6d8f6-665">ColumnName</span></span>|<span data-ttu-id="6d8f6-666">DataType</span><span class="sxs-lookup"><span data-stu-id="6d8f6-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d8f6-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-667">TABLE_CATALOG</span></span>|<span data-ttu-id="6d8f6-668">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-668">String</span></span>|  
|<span data-ttu-id="6d8f6-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d8f6-670">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-670">String</span></span>|  
|<span data-ttu-id="6d8f6-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-671">TABLE_NAME</span></span>|<span data-ttu-id="6d8f6-672">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-672">String</span></span>|  
|<span data-ttu-id="6d8f6-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d8f6-673">INDEX_CATALOG</span></span>|<span data-ttu-id="6d8f6-674">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-674">String</span></span>|  
|<span data-ttu-id="6d8f6-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d8f6-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="6d8f6-676">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-676">String</span></span>|  
|<span data-ttu-id="6d8f6-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-677">INDEX_NAME</span></span>|<span data-ttu-id="6d8f6-678">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-678">String</span></span>|  
|<span data-ttu-id="6d8f6-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6d8f6-679">PRIMARY_KEY</span></span>|<span data-ttu-id="6d8f6-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-680">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-681">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-681">UNIQUE</span></span>|<span data-ttu-id="6d8f6-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-682">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6d8f6-683">CLUSTERED</span></span>|<span data-ttu-id="6d8f6-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-684">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-685">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-685">TYPE</span></span>|<span data-ttu-id="6d8f6-686">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-686">Int32</span></span>|  
|<span data-ttu-id="6d8f6-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6d8f6-687">FILL_FACTOR</span></span>|<span data-ttu-id="6d8f6-688">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-688">Int32</span></span>|  
|<span data-ttu-id="6d8f6-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-689">INITIAL_SIZE</span></span>|<span data-ttu-id="6d8f6-690">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-690">Int32</span></span>|  
|<span data-ttu-id="6d8f6-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-691">NULLS</span></span>|<span data-ttu-id="6d8f6-692">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-692">Int32</span></span>|  
|<span data-ttu-id="6d8f6-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6d8f6-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-694">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-695">AUTO_UPDATE</span></span>|<span data-ttu-id="6d8f6-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-696">Boolean</span></span>|  
|<span data-ttu-id="6d8f6-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-697">NULL_COLLATION</span></span>|<span data-ttu-id="6d8f6-698">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-698">Int32</span></span>|  
|<span data-ttu-id="6d8f6-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d8f6-700">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-700">Int64</span></span>|  
|<span data-ttu-id="6d8f6-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d8f6-701">COLUMN_NAME</span></span>|<span data-ttu-id="6d8f6-702">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-702">String</span></span>|  
|<span data-ttu-id="6d8f6-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-703">COLUMN_GUID</span></span>|<span data-ttu-id="6d8f6-704">Guid</span><span class="sxs-lookup"><span data-stu-id="6d8f6-704">Guid</span></span>|  
|<span data-ttu-id="6d8f6-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d8f6-705">COLUMN_PROPID</span></span>|<span data-ttu-id="6d8f6-706">Int64</span><span class="sxs-lookup"><span data-stu-id="6d8f6-706">Int64</span></span>|  
|<span data-ttu-id="6d8f6-707">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-707">COLLATION</span></span>|<span data-ttu-id="6d8f6-708">Int16</span><span class="sxs-lookup"><span data-stu-id="6d8f6-708">Int16</span></span>|  
|<span data-ttu-id="6d8f6-709">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="6d8f6-709">CARDINALITY</span></span>|<span data-ttu-id="6d8f6-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="6d8f6-710">Decimal</span></span>|  
|<span data-ttu-id="6d8f6-711">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="6d8f6-711">PAGES</span></span>|<span data-ttu-id="6d8f6-712">Int32</span><span class="sxs-lookup"><span data-stu-id="6d8f6-712">Int32</span></span>|  
|<span data-ttu-id="6d8f6-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6d8f6-713">FILTER_CONDITION</span></span>|<span data-ttu-id="6d8f6-714">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6d8f6-714">String</span></span>|  
|<span data-ttu-id="6d8f6-715">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="6d8f6-715">INTEGRATED</span></span>|<span data-ttu-id="6d8f6-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d8f6-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d8f6-717">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d8f6-717">See Also</span></span>  
 <span data-ttu-id="6d8f6-718">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="6d8f6-718">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
