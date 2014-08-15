###git use experience

####when git push, prompt fatal: Reference has invalid format: 'refs/heads/master (linux's conflicted copy 2014...)

- solution

		cd repository
		find . -type f -name "* conflicted copy*" -exec rm -f {} \;
		awk '!/conflicted/' .git/packed-refs > temp && mv temp .git/packed-refs