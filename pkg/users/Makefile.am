usersdir = $(pkgdatadir)/users
nodist_users_DATA = \
	pkg/users/bundle.min.js.gz \
	pkg/users/index.min.html.gz \
	pkg/users/users.min.css.gz \
	$(NULL)
users_DATA = \
	pkg/users/manifest.json \
	$(NULL)

users_SCRIPTS = \
	pkg/users/ssh-add-public-key.sh \
	pkg/users/ssh-list-public-keys.sh \
	$(NULL)

usersdebugdir = $(debugdir)$(usersdir)
usersdebug_DATA = \
	pkg/users/authorized-keys.js \
	pkg/users/bundle.js \
	pkg/users/index.html \
	pkg/users/local.js \
	pkg/users/mustache.js \
	pkg/users/patterns.js \
	pkg/users/users.css \
	$(users_SCRIPTS) \
	$(NULL)

users_BUNDLEFILES = \
	pkg/users/authorized-keys.min.js \
	pkg/users/local.min.js \
	pkg/users/mustache.min.js \
	pkg/users/patterns.min.js \
	$(NULL)

users_BUNDLE = \
	$(users_BUNDLEFILES) \
	$(users_SCRIPTS) \
	$(NULL)

pkg/users/bundle.min.js: $(users_BUNDLE)
	$(AM_V_GEN) $(srcdir)/tools/missing $(srcdir)/tools/jsbundle $@ $^

# Ugliness to be solved by webpack in the future
pkg/users/mustache.min.js: pkg/users/mustache.js
	$(MIN_JS_RULE)

users_TESTS = \
	pkg/users/test-list-public-keys.sh \
	$(NULL)

TESTS += $(users_TESTS)

CLEANFILES += \
	pkg/users/bundle.min.js \
	pkg/users/index.min.html \
	pkg/users/users.min.css \
	$(users_BUNDLEFILES) \
	$(nodist_users_DATA) \
	$(NULL)

EXTRA_DIST += \
	pkg/users/mock \
	pkg/users/bundle.min.js \
	pkg/users/index.min.html \
	pkg/users/users.min.css \
	$(users_BUNDLE) \
	$(NULL)
