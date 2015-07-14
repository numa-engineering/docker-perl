# NAME

Net::Docker - Interface to the Docker API

# SYNOPSIS

    use Net::Docker;

    my $api = Net::Docker->new;

    my $id = $api->create(
        Image       => 'ubuntu',
        Cmd         => ['/bin/bash'],
        AttachStdin => \1,
        OpenStdin   => \1,
        Name        => 'my-container',
    );

    say $id;
    $api->start($id);

    my $cv = $api->streaming_logs($id,
        stream => 1, logs   => 1,
        stdin  => 1, stderr => 1, stdout => 1,
        in_fh  => \*STDIN, out_fh => \*STDOUT,
    );
    $cv->recv;

# DESCRIPTION

Perl module for using the Docker Remote API.

# AUTHOR

Peter Stuifzand <peter@stuifzand.eu>

# COPYRIGHT

Copyright 2013-2014 - Peter Stuifzand

# LICENSE

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# SEE ALSO

[http://docker.com](http://docker.com)
