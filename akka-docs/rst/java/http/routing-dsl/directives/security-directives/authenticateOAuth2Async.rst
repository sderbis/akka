.. _-authenticateOAuth2Async-java-:

authenticateOAuth2Async
=======================
Wraps the inner route with OAuth Bearer Token authentication support using a given ``AsyncAuthenticator<T>``.

Description
-----------
Provides support for extracting the so-called "*Bearer Token*" from the :class:`Authorization` HTTP Header,
which is used to initiate an OAuth2 authorization.

.. warning::
  This directive does not implement the complete OAuth2 protocol, but instead enables implementing it,
  by extracting the needed token from the HTTP headers.

Given a function returning ``Some<T>`` upon successful authentication and ``None`` otherwise,
respectively applies the inner route or rejects the request with a :class:`AuthenticationFailedRejection` rejection,
which by default is mapped to an ``401 Unauthorized`` response.

See also :ref:`-authenticateOAuth2-java-` if the authorization operation is rather quick, and does not have to execute asynchronously.

See :ref:`credentials-and-timing-attacks-java` for details about verifying the secret.

For more information on how OAuth2 works see `RFC 6750`_.

.. _RFC 6750: https://tools.ietf.org/html/rfc6750


Example
-------

Usage in code is exactly the same as :ref:`-authenticateBasicAsync-java-`,
with the difference that one must validate the token as OAuth2 dictates (which is currently not part of Akka HTTP itself).
