PORTNAME=	conduit
DISTVERSIONPREFIX=	v
DISTVERSION=	0.2.0
PORTREVISION=	2
CATEGORIES=	net-im
PKGNAMEPREFIX=	matrix-

MAINTAINER=	ashish@FreeBSD.org
COMMENT=	Simple, fast and reliable chat server powered by Matrix

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		cargo
USE_RC_SUBR=	${PORTNAME}
USERS=		${PORTNAME}
GROUPS=		${USERS}
SUBS=		DBDIR=${DBDIR} \
		USERS=${USERS} \
		GROUPS=${GROUPS} \
		PORTNAME=${PORTNAME}
PLIST_SUB=	${SUBS}
SUB_LIST=	${SUBS}
SUB_FILES=	pkg-message pkg-install
DBDIR=		/var/db/${PORTNAME}

USE_GITLAB=	yes
GL_ACCOUNT=	famedly
GL_COMMIT=	0d6ae2e1e74ee33fbc8dfcec01a8902e0a4d65d3
CARGO_CRATES=	adler32-1.2.0 \
		ahash-0.7.4 \
		aho-corasick-0.7.18 \
		ansi_term-0.12.1 \
		arrayref-0.3.6 \
		arrayvec-0.5.2 \
		assign-1.1.1 \
		async-stream-0.3.2 \
		async-stream-impl-0.3.2 \
		async-trait-0.1.51 \
		atomic-0.5.0 \
		atty-0.2.14 \
		autocfg-1.0.1 \
		base-x-0.2.8 \
		base64-0.12.3 \
		base64-0.13.0 \
		binascii-0.1.4 \
		bincode-1.3.3 \
		bitflags-1.3.2 \
		blake2b_simd-0.5.11 \
		block-buffer-0.9.0 \
		bumpalo-3.7.0 \
		bytemuck-1.7.2 \
		byteorder-1.4.3 \
		bytes-1.1.0 \
		cc-1.0.70 \
		cfg-if-0.1.10 \
		cfg-if-1.0.0 \
		chrono-0.4.19 \
		color_quant-1.1.0 \
		const-oid-0.6.0 \
		const_fn-0.4.8 \
		constant_time_eq-0.1.5 \
		cookie-0.15.1 \
		core-foundation-0.9.1 \
		core-foundation-sys-0.8.2 \
		cpufeatures-0.2.1 \
		crc32fast-1.2.1 \
		crossbeam-0.8.1 \
		crossbeam-channel-0.5.1 \
		crossbeam-deque-0.8.1 \
		crossbeam-epoch-0.9.5 \
		crossbeam-queue-0.1.2 \
		crossbeam-queue-0.3.2 \
		crossbeam-utils-0.6.6 \
		crossbeam-utils-0.8.5 \
		curve25519-dalek-3.2.0 \
		data-encoding-2.3.2 \
		deflate-0.8.6 \
		der-0.4.1 \
		devise-0.3.1 \
		devise_codegen-0.3.1 \
		devise_core-0.3.1 \
		digest-0.9.0 \
		directories-3.0.2 \
		dirs-sys-0.3.6 \
		discard-1.0.4 \
		dtoa-0.4.8 \
		ed25519-1.2.0 \
		ed25519-dalek-1.0.1 \
		either-1.6.1 \
		encoding_rs-0.8.28 \
		enum-as-inner-0.3.3 \
		env_logger-0.7.1 \
		fallible-iterator-0.2.0 \
		fallible-streaming-iterator-0.1.9 \
		figment-0.10.6 \
		fnv-1.0.7 \
		form_urlencoded-1.0.1 \
		fs2-0.4.3 \
		futures-0.3.17 \
		futures-channel-0.3.17 \
		futures-core-0.3.17 \
		futures-executor-0.3.17 \
		futures-io-0.3.17 \
		futures-macro-0.3.17 \
		futures-sink-0.3.17 \
		futures-task-0.3.17 \
		futures-util-0.3.17 \
		fxhash-0.2.1 \
		generator-0.7.0 \
		generic-array-0.14.4 \
		getrandom-0.1.16 \
		getrandom-0.2.3 \
		gif-0.11.2 \
		glob-0.3.0 \
		h2-0.3.4 \
		hashbrown-0.11.2 \
		hashlink-0.7.0 \
		heck-0.3.3 \
		hermit-abi-0.1.19 \
		hostname-0.3.1 \
		http-0.2.4 \
		http-body-0.4.3 \
		httparse-1.5.1 \
		httpdate-1.0.1 \
		humantime-1.3.0 \
		hyper-0.14.12 \
		hyper-rustls-0.22.1 \
		idna-0.2.3 \
		image-0.23.14 \
		indexmap-1.7.0 \
		indoc-1.0.3 \
		inlinable_string-0.1.14 \
		instant-0.1.10 \
		integer-encoding-1.1.7 \
		ipconfig-0.2.2 \
		ipnet-2.3.1 \
		itertools-0.9.0 \
		itertools-0.10.1 \
		itoa-0.4.8 \
		jobserver-0.1.24 \
		jpeg-decoder-0.1.22 \
		js-sys-0.3.53 \
		js_int-0.2.1 \
		jsonwebtoken-7.2.0 \
		lazy_static-1.4.0 \
		libc-0.2.101 \
		libsqlite3-sys-0.22.2 \
		linked-hash-map-0.5.4 \
		lmdb-rkv-sys-0.11.0 \
		lock_api-0.4.5 \
		log-0.4.14 \
		loom-0.5.1 \
		lru-cache-0.1.2 \
		maplit-1.0.2 \
		match_cfg-0.1.0 \
		matchers-0.0.1 \
		matches-0.1.9 \
		memchr-2.4.1 \
		memoffset-0.6.4 \
		mime-0.3.16 \
		miniz_oxide-0.3.7 \
		mio-0.7.13 \
		miow-0.3.7 \
		multer-2.0.1 \
		ntapi-0.3.6 \
		num-bigint-0.2.6 \
		num-integer-0.1.44 \
		num-iter-0.1.42 \
		num-rational-0.3.2 \
		num-traits-0.2.14 \
		num_cpus-1.13.0 \
		once_cell-1.8.0 \
		opaque-debug-0.3.0 \
		openssl-probe-0.1.4 \
		opentelemetry-0.16.0 \
		opentelemetry-jaeger-0.15.0 \
		opentelemetry-semantic-conventions-0.8.0 \
		ordered-float-1.1.1 \
		page_size-0.4.2 \
		parking_lot-0.11.2 \
		parking_lot_core-0.8.5 \
		paste-1.0.5 \
		pear-0.2.3 \
		pear_codegen-0.2.3 \
		pem-0.8.3 \
		percent-encoding-2.1.0 \
		pin-project-1.0.8 \
		pin-project-internal-1.0.8 \
		pin-project-lite-0.2.7 \
		pin-utils-0.1.0 \
		pkcs8-0.7.5 \
		pkg-config-0.3.19 \
		png-0.16.8 \
		ppv-lite86-0.2.10 \
		pretty_env_logger-0.4.0 \
		proc-macro-crate-1.0.0 \
		proc-macro-hack-0.5.19 \
		proc-macro-nested-0.1.7 \
		proc-macro2-1.0.29 \
		proc-macro2-diagnostics-0.9.1 \
		quick-error-1.2.3 \
		quote-1.0.9 \
		rand-0.7.3 \
		rand-0.8.4 \
		rand_chacha-0.2.2 \
		rand_chacha-0.3.1 \
		rand_core-0.5.1 \
		rand_core-0.6.3 \
		rand_hc-0.2.0 \
		rand_hc-0.3.1 \
		redox_syscall-0.2.10 \
		redox_users-0.4.0 \
		ref-cast-1.0.6 \
		ref-cast-impl-1.0.6 \
		regex-1.5.4 \
		regex-automata-0.1.10 \
		regex-syntax-0.6.25 \
		remove_dir_all-0.5.3 \
		reqwest-0.11.4 \
		resolv-conf-0.7.0 \
		ring-0.16.20 \
		rocket-0.5.0-rc.1 \
		rocket_codegen-0.5.0-rc.1 \
		rocket_http-0.5.0-rc.1 \
		ruma-0.4.0 \
		ruma-api-0.18.3 \
		ruma-api-macros-0.18.3 \
		ruma-appservice-api-0.4.0 \
		ruma-client-api-0.12.2 \
		ruma-common-0.6.0 \
		ruma-events-0.24.5 \
		ruma-events-macros-0.24.5 \
		ruma-federation-api-0.3.1 \
		ruma-identifiers-0.20.0 \
		ruma-identifiers-macros-0.20.0 \
		ruma-identifiers-validation-0.5.0 \
		ruma-identity-service-api-0.3.0 \
		ruma-push-gateway-api-0.3.0 \
		ruma-serde-0.5.0 \
		ruma-serde-macros-0.5.0 \
		ruma-signatures-0.9.0 \
		ruma-state-res-0.4.1 \
		rusqlite-0.25.3 \
		rust-argon2-0.8.3 \
		rustc_version-0.2.3 \
		rustls-0.19.1 \
		rustls-native-certs-0.5.0 \
		rustversion-1.0.5 \
		ryu-1.0.5 \
		schannel-0.1.19 \
		scoped-tls-1.0.0 \
		scopeguard-1.1.0 \
		sct-0.6.1 \
		security-framework-2.4.2 \
		security-framework-sys-2.4.2 \
		semver-0.9.0 \
		semver-parser-0.7.0 \
		serde-1.0.130 \
		serde_derive-1.0.130 \
		serde_json-1.0.67 \
		serde_urlencoded-0.7.0 \
		serde_yaml-0.8.20 \
		sha1-0.6.0 \
		sha2-0.9.6 \
		sharded-slab-0.1.3 \
		signal-hook-registry-1.4.0 \
		signature-1.3.1 \
		simple_asn1-0.4.1 \
		slab-0.4.4 \
		sled-0.34.6 \
		smallvec-1.6.1 \
		socket2-0.3.19 \
		socket2-0.4.1 \
		spin-0.5.2 \
		spin-0.9.2 \
		spki-0.4.0 \
		stable-pattern-0.1.0 \
		standback-0.2.17 \
		state-0.5.2 \
		stdweb-0.4.20 \
		stdweb-derive-0.5.3 \
		stdweb-internal-macros-0.2.9 \
		stdweb-internal-runtime-0.1.5 \
		subtle-2.4.1 \
		syn-1.0.75 \
		synchronoise-1.0.0 \
		synstructure-0.12.5 \
		tempfile-3.2.0 \
		termcolor-1.1.2 \
		thiserror-1.0.28 \
		thiserror-impl-1.0.28 \
		thread_local-1.1.3 \
		threadpool-1.8.1 \
		thrift-0.13.0 \
		time-0.1.43 \
		time-0.2.27 \
		time-macros-0.1.1 \
		time-macros-impl-0.1.2 \
		tinyvec-1.3.1 \
		tinyvec_macros-0.1.0 \
		tokio-1.11.0 \
		tokio-macros-1.3.0 \
		tokio-rustls-0.22.0 \
		tokio-socks-0.5.1 \
		tokio-stream-0.1.7 \
		tokio-util-0.6.7 \
		toml-0.5.8 \
		tower-service-0.3.1 \
		tracing-0.1.26 \
		tracing-attributes-0.1.15 \
		tracing-core-0.1.19 \
		tracing-flame-0.1.0 \
		tracing-log-0.1.2 \
		tracing-opentelemetry-0.15.0 \
		tracing-serde-0.1.2 \
		tracing-subscriber-0.2.20 \
		trust-dns-proto-0.20.3 \
		trust-dns-resolver-0.20.3 \
		try-lock-0.2.3 \
		twoway-0.2.2 \
		typenum-1.14.0 \
		ubyte-0.10.1 \
		uncased-0.9.6 \
		unchecked-index-0.2.2 \
		unicode-bidi-0.3.6 \
		unicode-normalization-0.1.19 \
		unicode-segmentation-1.8.0 \
		unicode-xid-0.2.2 \
		unindent-0.1.7 \
		untrusted-0.7.1 \
		url-2.2.2 \
		vcpkg-0.2.15 \
		version_check-0.9.3 \
		want-0.3.0 \
		wasi-0.9.0+wasi-snapshot-preview1 \
		wasi-0.10.2+wasi-snapshot-preview1 \
		wasm-bindgen-0.2.76 \
		wasm-bindgen-backend-0.2.76 \
		wasm-bindgen-futures-0.4.26 \
		wasm-bindgen-macro-0.2.76 \
		wasm-bindgen-macro-support-0.2.76 \
		wasm-bindgen-shared-0.2.76 \
		web-sys-0.3.53 \
		webpki-0.21.4 \
		webpki-0.22.0 \
		weezl-0.1.5 \
		widestring-0.4.3 \
		wildmatch-2.1.0 \
		winapi-0.3.9 \
		winapi-i686-pc-windows-gnu-0.4.0 \
		winapi-util-0.1.5 \
		winapi-x86_64-pc-windows-gnu-0.4.0 \
		winreg-0.6.2 \
		winreg-0.7.0 \
		yaml-rust-0.4.5 \
		yansi-0.5.0 \
		zeroize-1.4.1 \
		zeroize_derive-1.1.0 \
		zstd-0.5.4+zstd.1.4.7 \
		zstd-safe-2.0.6+zstd.1.4.7 \
		zstd-sys-1.4.18+zstd.1.4.7 \
		heed,heed-traits,heed-types@git+https://github.com/timokoesters/heed.git?rev=f6f825da7fb2c758867e05ad973ef800a6fe1d5d\#f6f825da7fb2c758867e05ad973ef800a6fe1d5d

post-patch:
	@${REINPLACE_CMD} -e 's,/etc/conduit.toml,${PREFIX}/etc/conduit.toml,' \
		${WRKSRC}/src/main.rs
	@${REINPLACE_CMD} -e 's,/var/lib/conduit,${DBDIR},' \
		${WRKSRC}/conduit-example.toml

post-install:
	${INSTALL_DATA} ${WRKSRC}/conduit-example.toml ${STAGEDIR}${PREFIX}/etc/${PORTNAME}.toml.sample
	@${MKDIR} ${STAGEDIR}${DBDIR}

.include <bsd.port.mk>
