\ Sane Forth Standard

Taking inspiration from the simplicity of the scheme standard, and with
admiration of the unified Emacs Lisp ecosystem, Saneforth looks to bridge
the gap between forth and the modern age - creating a dynamic and growing
ecosystem of tiny peices of software that enjoy the benifits of the tiny,
infinintely extendable forth language.

The scope of this project is large in abition, and small in implimentation,

The roadmap looks something like this:

	1. Release version 0.0 of the standard
	2. Release an ultra-tiny non-optomized interpriter, written in C89
	3. Play around for a couple weeks/months, itteratively improving

		(v0.1, v0.2, v0.3...)

	4. Release version 1.0 of the standard
	5. Release a "Standard Library"

		- Distinguish between 2 types of "Libraries"

			> Libraries -- (designated as "lib")
				Libraries follow a pattern <library>:<word>, and seperate
				themselves from the base lang.
				(ie. file:write)

				They add well-defined words to the lang, and do not change
				base functionality of the lang.

			> Extension Libraries -- (designated as "exlib")
				Extension libs are seprate to warn the user, these libraries
				take advantage of the full power of forth.
				They are not well-defined, and are allowed to have
				single-character words, prefix words (Features[1]) , and even
				extend and replace base-words.

				There is no limit to elib's power, so be very very carful with
				them.

				(example
					" - prefix word --	reads until the next " and compiles that
										into a null-terminated string.)

	6. Start developing the ecosystem
			(taking advantage of the power of forth to impliment everything in
			 trivial sloc, making it almost infinitely hackable and extendable)
		- Text editor (>300 sloc)
		- Core util replacement {lib} (few thousand sloc)
		- Shell replacement {elib} (>150 sloc)
		- Text-based browser
		- Much much more.

		Note:	I would like take a second to explain how forth programs are
				written. Typically you write a command language for the specific
				task you are doing (for example: editing) and then you
				write features around that language.

				(so like
					up
					down
					left
					right
					writechar
					grabchar
					copy
					paste
					etc...)

				For the text editor, you would probably add an interaction
				layer for the input that:
					- updates a visual repersentation of the doc
					- binds short-cuts to specific keys or key-combinations
				 	  (like a tiling wm)

				However, it is imperative that you give the user access to the
				underlying forth shell. This is what turns the editor from a
				cool toy, to the perfect hackers lanugage. Not seperating
				editor scripting from the editor itself, this allows for
				infinitely powerful scripts, even changing behavior at runtime.
				(ie. simple example, redefine `k` as "go up 2" instead of 1)


	Note:	All of this up until this point, is utterly microscopic amounts of
			code. >3000 sloc type small.
			Like I said, large ambition, tiny implimentation, code is art and
			should be built tiny, then audited and edited to utter perfection.
			None of this should take very much work at all.

	7. Optomizing compiler
		(biggest and hardest part of the project)
		- Lookahead
		- Loop unrolling
		- Way more shit than peephole