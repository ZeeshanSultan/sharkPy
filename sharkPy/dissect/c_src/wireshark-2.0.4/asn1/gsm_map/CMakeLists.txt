# CMakeLists.txt
#
# Wireshark - Network traffic analyzer
# By Gerald Combs <gerald@wireshark.org>
# Copyright 1998 Gerald Combs
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
#

set( PROTOCOL_NAME gsm_map )

set( PROTO_OPT _EMPTY_ )

set( EXPORT_FILES
	${PROTOCOL_NAME}-exp.cnf
)

set( EXT_ASN_FILE_LIST
	../ros/Remote-Operations-Information-Objects.asn
)

set( DATATYPES_ASN_FILES
	MAP-ExtensionDataTypes.asn
	MAP-CommonDataTypes.asn
	MAP-SS-DataTypes.asn
	MAP-ER-DataTypes.asn
	MAP-SM-DataTypes.asn
	MAP-OM-DataTypes.asn
	MAP-MS-DataTypes.asn
	MAP-CH-DataTypes.asn
	MAP-LCS-DataTypes.asn
	MAP-GR-DataTypes.asn
)

set( OPERATIONS_ASN_FILES
	MAP-LocationServiceOperations.asn
	MAP-Group-Call-Operations.asn
	MAP-ShortMessageServiceOperations.asn
	MAP-SupplementaryServiceOperations.asn
	MAP-CallHandlingOperations.asn
	MAP-OperationAndMaintenanceOperations.asn
	MAP-MobileServiceOperations.asn
)

set( SS_ASN_FILES
	SS-DataTypes.asn
	SS-Operations.asn
)

set( PROPRIETARY_ASN_FILES
	Ericsson.asn
	Nokia.asn
)

set( ASN_FILE_LIST
	MobileDomainDefinitions.asn
	MAP-ApplicationContexts.asn
	MAP-SS-Code.asn
	MAP-BS-Code.asn
	MAP-TS-Code.asn
	${DATATYPES_ASN_FILES}
	MAP-DialogueInformation.asn
	${OPERATIONS_ASN_FILES}
	MAP-Errors.asn
	MAP-Protocol.asn
	GSMMAP.asn
	${SS_ASN_FILES}
	${PROPRIETARY_ASN_FILES}
)

set( EXTRA_DIST
	${ASN_FILE_LIST}
	packet-${PROTOCOL_NAME}-template.c
	packet-${PROTOCOL_NAME}-template.h
	${PROTOCOL_NAME}.cnf
)

set( SRC_FILES
	${EXTRA_DIST}
	${EXT_ASN_FILE_LIST}
)

set( A2W_FLAGS -b )

set( EXTRA_CNF
)

ASN2WRS()

